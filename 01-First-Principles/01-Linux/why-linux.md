# Introduction to the world of Linux

I get it, most of the people prefer the comfort of an UI based OS to a bare skeletal structure of Linux.
Since you're starting out on programming in an unknown territory, you need to gain mastery over a few core concepts of Linux that will recur every now and then. I hope you have a distribution of Linux installed on your system.
You can find the latest distribution here at https://ubuntu.com/

## GNU and Terminal
Large portions of GNU/Linux functionality are achieved using the terminal.
Most distributions of Linux include terminal emulators that allow users to interact with a shell from their desktop environment.
A shell is a commandline interpreter that executes user inputted commands. Bash (Bourne Again SHell) is a common default shell among many Linux distributions and is the default shell for macOS.

* Press `Ctrl + Alt + T` to open up a terminal

### Text Manipulation

* `Ctrl + U` - cuts the line from the current position to the beginning of the line, adding it to the clipboard.
* `Ctrl + K` - cuts the line from the current position to the end of the line, adding it to the clipboard.
* `Ctrl + Y` - pastes the last thing from the clipboard that you cut recently
* `Alt + L` - makes lowercase from cursor to end of word.
* `Alt + U` - Make uppercase from cursor to end of word.
* `Alt + D` - Delete to end of word starting at cursor
* `Alt + .` - Prints the last word written in previous command.

### Accessing Command History
* `Ctrl + R` - lets you search through previously used commands.
* `Ctrl + G` - to leave history searching mode without running a command.
* `Ctrl + J` - lets you copy current matched command to command line without running it

### Terminal Controls
* `Ctrl + z` - suspends (pause) currently running foreground process, which returns shell prompt. Use `bg` command allowing that process to run in the background and to again bring that process to foreground, use `fg` command
* `Ctrl + C` - ends the currently running process.
* `Ctrl + L` - clears the screen, similar to the clear command.
* `Ctrl + S` - stops all output to the screen

### Close Terminal
* `Ctrl + Shift + W` - To close terminal tab.
* `Ctrl + Shift + Q` - To close entire terminal

## File Management

### Directory navigation
* `pwd` - Get the full path of the current working directory.
* `cd-` - Navigate to the last directory you were working in.
* `cd ~` - or just cd Navigate to the current user's home directory.
* `cd ..` - Go to the parent directory of current directory

### Listing files inside a directory
* `ls -l` - To list the files and directories in the current directory.
* `ls -a` - to list all the files including the hidden ones
* `tree` - Will generate a tree representation of the file system starting from the current directory.

### Moving files from one place to another
* `cp -p source destination` - Will copy the file from source to destination. -p stands for preservation, it preserves the original attributes of file while copying like file owner, timestamp, group, permissions.
* `mv file1 file2` - In Linux there is no rename command as such. Hence mv moves/renames the file1 to file2
* `rm -i filename` - Confirms every file removal action
* `rm -rf dir-name` - Will remove the directory dir recursively, ignoring non-existent files and will never prompt for anything.
* Other important commands include `mkdir` to create a new dir, `rmdir` to remove a directory if it is empty, `touch filename` - to create a new file.

### Changing file permissions
* `chmod <specification> filename` - Changes the file permissions.
  Specifications = **u** `user`, **g** `group`, **o** `other`, **+ add permission**, **- remove**, **r** `read`, **w** `write`, **x** `execute`.
* `chmod -R ` - To recursively apply the changes

## Basic Linux Utilities

### User related
* `hostname` - Shows the hostname of a system
* `hostname -f` - displays Fully Qualified Domain Name (FQDN) of the system.
* `passwd` - change password of current user.
* `whoami` - Username of the users logged in at the terminal.
* `last` - Who recently used the system.
* `last root` - When was the last time root logged in as user.
* `lastb` - Shows all bad login attempts into the system

### Process related information
* `top` - List all processes sorted by their current system resource usage. Use q key to exit top.
* `ps` - List processes currently running on current shell session
* `ps -u root` - List all of the processes and commands root is running

### Searching for files via name
* `find /location -name '*.filename'` - searches for the file in that location
* `grep 'Keyword' /location` - searches for the Keyword in the location
* `grep -R 'Keyword' /location` - searches for the Keyword recursively in the location

### File Manipulation
* `touch filename` - creates a file by the filename specified
* `cat filename` - see the contents of the file without opening it
* `head filename` - view the first few lines of the file
* `tail filename` - view the last few lines of the file
* `less filename` - view the content of a file with paging

File permissions are in the format : `drwxrwxrwx`
* The first character represents the file type d if it's a directory - otherwise.
* The next three rwx are the permissions the user has over the file
* The next three are the permissions the group has over the file
* The last three are the permissions everyone else has over the file.

The `r` of rwx stands for if a file can be read, the `w` represents if the file can be modified, and the `x` stands for if the file can be executed. If any permission isn't granted a - will be in place of r, w, or x.
r = 4, w = 2, and x = 1

Examples:
* **Owner** `rwx` = 4+2+1 = 7
* **Group** `r-x` = 4+0+1 = 5
* **Other** `r-x` = 4+0+1 = 5

## Shell Utilities

### Customize
Default command prompt looks something like this: user@host ~ $
You can use `PS1='zeppelin $ '` zeppelin $ will show the shell prompt the way you like
Also checkout Figlet for more customizing

### history
* `~/.bash_history` - stores last 500 commands/events used on the shell
* `history` - will show the command history
* `history | grep <key-word>` - will show all the commands in history having keyword <key-word>

### Command aliasing
* `alias command_alias` = 'actual_command'
Now use the command_alias in place of the actual command whenever needed

### Locating a file on your system
say you are looking for the file mykey.pem:
You can use

```
locate mykey.pem
```

If this doesn't work, fall back to find

```
find / -name mykey.pem -print
```

### Checking disk usage

* `du` - summarizes disk usage of the set of FILEs, recursively for directories.
* `du -sh *` - summarizes disk usages of the files in the current directory
* `du -sh .[!.]* *` - summarizes disk usage including hidden Files and  you can add total to the output by adding `-c` option as `du -sch .[!.]* *``
* `sudo du -sch /.[!.]* /*` - investigate root dir for disk usage


## System Information
* `mpstat` - get processors related statistics
* `free` -  to show amount of (remaining) RAM but to see all statistic including I/O operations use `vmstat`
* `iostat` -  get general information about your disk operations in real timestamp
* `lscpu` - Get all the cpu information
* `lshw` - a small tool to extract detailed information on the hardware configuration of the machine
* `dmidecode -q | less` - to show BIOS information

## Process Information
* `ps -e -o pid, args --forest` - List processes in a hierarchy
* `ps -e -o pcpu,cpu,nice,state,cputime,args --sort pcpu | sed '/^ 0.0 /d'` - List processes sorted by % cpu usage
* ` ps -e -orss=,args= | sort -b -k1,1n` - List processes sorted by mem (KB) usage.
* `htop` - for more interactive monitoring

## File compression and decompression

Common Options
```
-c --create Create a new archive.
-x --extract Extract files from an archive.
-t --list List the contents of an archive.
-f --file=ARCHIVE Use archive file or dir ARCHIVE.
-v --verbose Verbosely list files processed.
```
Compression Options
```
-a --auto-compress
-j --bzip2 Filter the archive through bzip2.
-J --xz --lzma Filter the archive through xz.
-z --gzip Filter the archive through gzip.
```

* `tar -cf ./my-archive.tar ./my-folder/` - creates a simple archive of a folder
* `tar -cvf ./my-archive.tar ./my-folder` - Verbose output shows which files and directories are added to the archive
* `tar -czf ./my-archive.tar.gz ./my-folder/` -  archiving a folder compressed 'gzip', you have to use the -z option
* `tar -xf archive-name.tar` - extract a folder from an archive in the current location
* `tar -xf archive-name.tar -C ./directory/destination` -  extract a folder from an archive to a specfic destination
* `tar -cf archive.tar ./my-folder/ --exclude="my-folder/sub1" --exclude="my-folder/sub3"` - you want to extract a folder, but you want to exclude one or several folders during the extraction

## Services

Get a list of services
* `service --status-all`

Listing services
* `systemctl` - To list running services
* `systemctl --failed` - To list failed services

Managing Targets (Similar to Runlevels in SysV)
* `systemctl get-default` - To find the default target for your system
* `systemctl set-default <target-name>` - To set the default target for your system

Managing services at runtime
* `systemctl start [service-name]`- To start a service
* `systemctl stop [service-name]` - To stop a service
* `systemctl restart [service-name]` - To restart a service
* `systemctl reload [service-name]` - To request service to reload its configuration
* `systemctl status [service-name]` - To show current status of a service

Managing autostart of services
* `systemctl is-enabled [service-name]` - To show whether a service is enabled on system boot
* `systemctl is-active [service-name]` - To show whether a service is currently active(running)
* `systemctl enable [service-name]` - To enable a service on system boot
* `systemctl disable [service-name]` - To disable a service on system boot

Restarting systemd
* `systemctl daemon-reload`
