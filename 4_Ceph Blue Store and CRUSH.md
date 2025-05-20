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