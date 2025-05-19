# Essential Linux Commands

## System Information
- **To Print Operating System name:**
  - `uname`
  
- **To Show system information:**
  - `uname -a` (Displays all system information)

## Navigation & File Management
- **To Print Working Directory:**
  - `pwd`
  
- **To Navigate to a different Directory:**
  - `cd <dir-path>`
    - `cd ..` (Go up one level)
    - `cd ~` (Go to home directory)
  
- **To display content of a Directory:**
  - `ls <dir-path>`
    - `ls` (Display content of current directory)
    - `ls -l <dir-path>` (Display content in detail)
    - `ls -a <dir-path>` (Show hidden files)
  
- **To Display content of a File:**
  - `cat <file>`
  
- **To Open a file in Vim editor:**
  - `vim <file>`
    - **In Normal Mode:**
      - `dd` (Delete line)
      - `yy` (Copy line)
      - `p` (Paste)
    - **In Insert Mode (press `i`):**
      - Type to insert text
    - **In Command Mode (press `:`):**
      - `:w` (Save)
      - `:q` (Quit)
      - `:wq` (Save and quit)

## File Operations
- **To Copy a file:**
  - `cp <source-file> <destination-file>`
  
- **To Move/Rename a file:**
  - `mv <source-file> <destination-file>`
  
- **To Remove a file:**
  - `rm <file>`
    - `rm -r <dir>` (Remove directory and contents)
    - `rm -f <file>` (Force remove without confirmation)
  
- **To Create a Directory:**
  - `mkdir <dir-name>`

## Searching & Filtering
- **To Filter words from file:**
  - `cat <file> | grep <filter-word>`
    - `grep -i <filter-word> <file>` (Case insensitive search)
  
- **To Search for files:**
  - `find <dir> -name <filter-string>`
  
- **To Compare two files:**
  - `diff <first-file> <second-file>`
  
- **To Count lines, words, or characters:**
  - `wc <file>`
    - `wc -l <file>` (Count lines)
    - `wc -w <file>` (Count words)
    - `wc -m <file>` (Count characters)

## Networking Commands
- **To Test connectivity:**
  - `ping <hostname>`
    - Example: `ping -c 4 google.com` (Limit to 4 packets)
  
- **To Transfer data from/to server:**
  - `curl <url>`
    - `curl -I <url>` (Get metadata of a URL)
  
- **To Display network statistics:**
  - `netstat -tuln`

## Process Management
- **To Show running processes:**
  - `ps`
    - `ps -ef` (Detailed process list)
    - `ps aux` (Another detailed process list)
  
- **To Monitor processes in real-time:**
  - `top`
  
- **To Terminate a process:**
  - `kill <pid>`

## Resource Management
- **To Show disk space:**
  - `df -h`
  
- **To Show memory usage:**
  - `free -h`

## Package Management (Debian-based systems)
- **To Update package list:**
  - `sudo apt update`
  
- **To Install a package:**
  - `sudo apt install <package-name>`
  
- **To Remove a package:**
  - `sudo apt remove <package-name>`
  
- **To Upgrade packages:**
  - `sudo apt upgrade`

## Miscellaneous
- **To Run a command as root:**
  - `sudo <command>`
  
- **To change file permissions:**
  - `chmod <permissions> <file>`
  
- **To view command history:**
  - `history`
  
- **To exit the terminal:**
  - `exit