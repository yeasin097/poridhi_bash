# Bash Commands Tutorial

Before we begin, we must clear two concepts: **directory** and **path**, to understand Bash commands better.

## What is a Directory?
A directory is a folder in any operating system. We use directories to store files and other directories.

## What is a Path?
A path specifies the location of a directory or a file. For example:
```
/home/poridhi/Desktop
```
It means that to find the Desktop directory, we have to go through `home`, then `poridhi`, and finally we will find `Desktop`.

### Types of Paths
1. **Absolute Path**: Starts from the root directory of the Linux filesystem. The command `pwd` (print working directory) prints the absolute path of a directory.
   ```bash
   poridhi@ubuntu:~$ pwd
   /home/poridhi
   ```

2. **Relative Path**: The location of a directory or a file relative to the current working directory. 
   Example:
   ```bash
   poridhi@ubuntu:~/bash$ ls
   Image
   poridhi@ubuntu:~/bash$ cd Image
   poridhi@ubuntu:~/bash/Image$ pwd
   /home/poridhi/bash/Image
   ```

## Fundamental Commands in Bash

### 1. `cd` (Change Directory)
Used to change the current working directory.

Examples:
```bash
poridhi@ubuntu:~$ cd /home/poridhi/Desktop
poridhi@ubuntu:~/Desktop$

poridhi@ubuntu:~/Desktop$ cd ..
poridhi@ubuntu:/home/poridhi$

poridhi@ubuntu:/home/poridhi$ cd ~
poridhi@ubuntu:~$

poridhi@ubuntu:~$ cd /tmp
poridhi@ubuntu:/tmp$
```

### 2. `ls` (List Directory Contents)
Lists the contents (files and folders) of a directory.

Examples:
```bash
poridhi@ubuntu:~$ ls
Desktop  Documents  Downloads

poridhi@ubuntu:~$ ls -a
.  ..  .bashrc  Desktop  Documents

poridhi@ubuntu:~$ ls -al

drwxr-xr-x 2 poridhi poridhi 4096 Jan  1 10:00 Desktop
-rw-r--r-- 1 poridhi poridhi  220 Jan  1 10:00 .bashrc
```

### 3. `mkdir` (Make Directory)
Creates a new directory.

Examples:
```bash
poridhi@ubuntu:~$ mkdir new_folder
poridhi@ubuntu:~$ ls
new_folder
```

### 4. `rmdir` (Remove Directory)
Removes an empty directory.

Examples:
```bash
poridhi@ubuntu:~$ ls
new_folder
poridhi@ubuntu:~$ rmdir new_folder
poridhi@ubuntu:~$ ls


```

### 5. `rm` (Remove)
Used to delete files or directories.

Examples:
```bash
# Remove a file
poridhi@ubuntu:~/Desktop$ rm file.txt

# Remove a directory and its contents
poridhi@ubuntu:~/Desktop$ rm -r old_folder

# Prompt before deleting
poridhi@ubuntu:~/Desktop$ rm -i file.txt
```

### 6. `touch`
Creates an empty file.

Examples:
```bash
poridhi@ubuntu:~/Desktop$ touch new_file.txt
poridhi@ubuntu:~/Desktop$ ls
new_file.txt

# Create multiple files
poridhi@ubuntu:~/Desktop$ touch file1.txt file2.txt
poridhi@ubuntu:~/Desktop$ ls
file1.txt  file2.txt
```

### 7. `cp` (Copy)
Copies files or directories.

Examples:
```bash
# Copy a file
poridhi@ubuntu:~/Desktop$ cp file1.txt /home/poridhi/Documents/

# Copy a directory
poridhi@ubuntu:~/Desktop$ cp -r folder1 /home/poridhi/Documents/

# Copy and preserve attributes
poridhi@ubuntu:~/Desktop$ cp -p file1.txt /home/poridhi/Documents/
```

### 8. `mv` (Move)
Moves or renames files and directories.

Examples:
```bash
# Move a file
poridhi@ubuntu:~/Desktop$ mv file1.txt /home/poridhi/Documents/

# Rename a file
poridhi@ubuntu:~/Desktop$ mv file1.txt file2.txt

# Move multiple files
poridhi@ubuntu:~/Desktop$ mv file1.txt file2.txt /home/poridhi/Documents/
```

### 9. `cat` (Concatenate)
Displays or combines files.

Examples:
```bash
# View a file
poridhi@ubuntu:~/Desktop$ cat file1.txt
these are the contents of file1.txt
# Combine files (> overwrite the content of combined.txt)
poridhi@ubuntu:~/Desktop$ cat file1.txt file2.txt > combined.txt
poridhi@ubuntu:~/Desktop$ cat combined.txt
these are the contents of file1.txt
and these are of file2.txt combined in combined.txt
# Append a file (>> appended so combined.txt's contents will stay)
poridhi@ubuntu:~/Desktop$ cat file1.txt >> combined.txt
poridhi@ubuntu:~/Desktop$ cat combined.txt
these are the contents of combined.txt then
contents of file1.txt added after combined.txt contents
```

### 10. `find`
Searches for files or directories.

Examples:
```bash
# Find all .txt files in the current directory
poridhi@ubuntu:~/Desktop$ find . -name "*.txt"
./dir1/file2.txt
./dir1/file1.txt
./dir1/file3.txt
./dir1/file4.txt
./file3.txt
./file4.txt

# Find a specific file
poridhi@ubuntu:~/Desktop$ find /home/poridhi -name "file1.txt"
./dir1/file1.txt
# Find by size, larger than 10MB
poridhi@ubuntu:~/Desktop$ find / -size +10M
/boot/vmlinuz-6.8.0-51-generic
/boot/initrd.img-6.8.0-50-generic
/boot/vmlinuz-6.8.0-50-generic
/boot/initrd.img-6.8.0-51-generic

# Exclude certain directories
poridhi@ubuntu:~/Desktop$ find . -name "*.log" -not -path "./backup/*"
```

### 11. `grep`
Searches for patterns in files.

Examples:
```bash
cat hello.txt
hello world
this is a word
this is a text to make grep simple
everything is simple
say hello to everyone
# Case-sensitive search
poridhi@ubuntu:~/Desktop$ grep "hel" hello.txt
hello world
say hello to everyone
poridhi@ubuntu:~/Desktop$ grep "every" hello.txt
everything is simple
say hello to everyone
# Case-insensitive search with line numbers
poridhi@ubuntu:~/Desktop$ grep -ni "GRe" hello.txt
2. this is a text to make grep example
# Search in multiple files
poridhi@ubuntu:~/Desktop$ grep "error" *.txt
# Search for a whole word only
poridhi@ubuntu:~/Desktop$ grep -w "every" hello.txt

poridhi@ubuntu:~/Desktop$ grep -w "everyone" hello.txt
say hello to everyone
```

### 12. `head`
Displays the first few lines of a file.

Examples:
```bash
# Default first 10 lines
poridhi@ubuntu:~/Desktop$ head hello.txt
hello world
say hello to everyone
.
.
.
# Custom number of lines, first 2 lines
poridhi@ubuntu:~/Desktop$ head -n 2 hello.txt
hello world
say hello to everyone
```



### 13. `tail`
Displays the last few lines of a file.

Examples:
```bash
# Default last 10 lines
poridhi@ubuntu:~/Desktop$ tail hello.txt
.
.
.
everything is simple
say hello to everyone
# Custom number of lines, 2 lines
poridhi@ubuntu:~/Desktop$ tail -n 2 hello.txt
everything is simple
say hello to everyone
```
### 14. `chmod`
Changes file or directory permissions.

Examples:
```bash
# Add execute permission for everyone
poridhi@ubuntu:~/Desktop$ chmod +x script.sh

# Change to full permissions for owner, group, and others
poridhi@ubuntu:~/Desktop$ chmod 777 file.txt

# Remove write permission for others
poridhi@ubuntu:~/Desktop$ chmod o-w file.txt
```
### 15. `chown`
Changes file or directory ownership.

Examples:
```bash
# Change ownership
poridhi@ubuntu:~/Desktop$ sudo chown user1:user1 file.txt

# Change ownership of a directory recursively
poridhi@ubuntu:~/Desktop$ sudo chown -R user1:user1 folder_name
```
### 16. `df` (Disk Free)
Shows disk space usage of file systems.

Examples:
```bash
# Show disk space usage in human-readable format
poridhi@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       50G   20G   30G  40% /

# Show disk space usage for a specific directory
poridhi@ubuntu:~$ df -h /home/poridhi
```

### 17. `du` (Disk Usage)
Shows disk usage of files and directories.

Examples:
```bash
# Show disk usage of a directory
poridhi@ubuntu:~$ du -sh /home/poridhi
1.5G    /home/poridhi

# Show disk usage of all files and directories
poridhi@ubuntu:~$ du -h --max-depth=1
```

### 18. `free`
Displays memory usage.

Examples:
```bash
# Show memory usage in human-readable format
poridhi@ubuntu:~$ free -h
              total        used        free      shared  buff/cache   available
Mem:           8.0G        2.5G        4.0G        200M        1.5G        5.2G
Swap:          2.0G          0B        2.0G
```

