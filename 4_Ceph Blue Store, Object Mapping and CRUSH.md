# Introduction to Blue Store
- Default starage backecd for Ceph OSDs (since Luminous).

- Write data directly to raw block device (no File System Layer)

- Replaces File Store which relied on XFS/EXT4

# WHy FIle Store?
- File Store used a POSIX File System - added complexity and overhead

- Inefficient write paths (journaling + metadata)

- Poor performance under high IO workloads

- Blue Store eliminates double write penalty

# BlueStore Architecture Overview
- Direct device I/O: Write directly to block devices

- Metadata stored in RocksDB

- Internak components:
    - WAL (Write-Ahead Log)
    - DB (RocksDB)
    - Slow/fast device support

- BlueStore Internal Layout:
    - DB: stores keys/metadata via RocksDB
    - WAL: for fast journaling
    - Main: actual object data and blobs

# Technologies used in Blue Store
- RockDB:
    - Embedded key-value store optimized for flash

- SPDK/aio/io_uring:
    - High-perfoamance I/O interfaces and SPDK from Intel

- CRC32/XXHash:
    - Data integrity checks

- Allocator algorithm:
    - Bitmap, freelist

- BLOB compression
    - zlib, snappy, zstd

# Performance Benefits
- Lower latency and higher throughput

- Reduced CPU usage

- Better small object handling

- Inline compression and checksums

- Efficient SSD use for DB/WAL seperation

# Deployment Considerations
- Fast devices (SSDs/NVMe) for DB/WAL

- Compression settings impact performance

- Device class seperation for tiered storage

- Fine-tune RocksDB parameters

# In Conclusion

- BlueStore = Higher performance Ceph storage backend than FileStore

- Direct I/O + RocksDB = faster, more reliable that FileStore

- Evolving with Ceph's ongoing development.

# What is the CRUSH Map?
- Defines topology and rules for placing data

- Deterministically maps PGs to OSDs

- Uses failure domains, device weights, rules

# How PGs are Mapped to OSDs
  1. Hash object -> PG

  2. Apply CRUSH rule -> ideal OSD set
 
  3. OSD Map checks current state -> actual acting set

# Limitations of CRUSH
- Deterministic placement causes problems:
    - When the cluster is full
    - When adding new hardware

  # OSDMap and PG Movement
  - CRUSH gives ideal placement
 
  - OSDMap tracks real-time status of OSDs
 
  - PGs move due to failures, rebalance, recovery
 
  - OSDMap determines where objects actually live
 
# pg_upmap/pg_upmap_items
- Used to overried CRUSH mapping for specific PGs

- pg_upmap: replace entire OSD set for a PG

- pg_upmapitem: replace specific OSD(s) in the acting set

- Useful for manual or balancer-driven rebalancing

# Determining the Primary OSD
- CRUSH determines an ordered list of OSDs

- First OSD = Primary

- Primary handles all client IO for PG

- OSDMap promotes secondary if primary fails

# Conclusion of Object Mapping and RUSH
- Hashing maps object to PGs

- CRUSH maps PGs to ideal OSD sets

- OSDMap tracks actual OSDs used

- pg_upmap allows fine-grained overrides

- Primary OSD is first in CRUSH list
