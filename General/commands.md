1. Real-Time Service Control
```
To change the state of a service on your currently running system, use start, stop, or restart, run the following command:


$ sudo systemctl start apache2

$ sudo systemctl stop apache2

$ sudo systemctl restart apache2

```

2. Boot-Time Configuration

```
To determine whether a service should launch automatically when the computer turns on, use enable or disable:


$ sudo systemctl enable apache2

$ sudo systemctl disable apache2
```

3. Monitoring Service Health
```
To check if a service is running, view its recent logs, or see its process ID (PID), use the status command:


$ sudo systemctl status apache2
```
4. 
```
cat: used to type out a file (or combine files).
head: used to show the first few lines of a file.
tail: used to show the last few lines of a file.
man: used to view documentation.
```
5. 

```
Rebooting and Shutting Down
The preferred method to shut down or reboot the system is to use the shutdown command. This sends a warning message, and then prevents further users from logging in. The init process will then control shutting down or rebooting the system. It is important to always shut down properly; failure to do so can result in damage to the system and/or loss of data.

The halt and poweroff commands issue shutdown -h to halt the system; reboot issues shutdown -r and causes the machine to reboot instead of just shutting down. Both rebooting and shutting down from the command line requires superuser (root) access.

When administering a multi-user system, you have the option of notifying all users prior to shutdown, as in:

$ sudo shutdown -h 10:00 "Shutting down for scheduled maintenance."

```

6. 
```
One way to locate programs is to employ the which utility. For example, to find out exactly where the diff program resides on the filesystem:

$ which diff
/usr/bin/diff

If which does not find the program, whereis is a good alternative because it looks for packages in a broader range of system directories:

$ whereis diff
diff: /usr/bin/diff /usr/share/man/man1/diff.1.gz /usr/share/man/man1p/diff.1p.gz
```

7. 
Accessing Directories
```
Command	    Result
pwd	        Displays the present working directory
cd ~ or cd	Change to your home directory; shortcut name is ~ (tilde)
cd ..	    Change to parent directory (..)
cd -	    Change to previous working directory; - (minus)
```

8. 
Traversing up and down the filesystem tree can get tedious. The tree command is a good way to get a bird’s-eye view of the filesystem tree. Use tree -d to view just the directories and to suppress listing file names
```
vboxuser@ubuntu26:~$ tree -d
.
├── Desktop
├── Documents
├── Downloads
├── Music
├── Pictures
├── Public
├── snap
│   ├── firmware-updater
│   │   ├── 226
│   │   ├── common
│   │   └── current -> 226
│   ├── prompting-client
│   │   ├── 204
│   │   ├── 222
│   │   ├── common
│   │   └── current -> 222
│   └── snapd-desktop-integration
│       ├── 361
│       ├── common
│       └── current -> 361
├── Templates
└── Videos
```

9. Exploring the Filesystem
```
Command	    Usage
cd /	    Changes your current directory to the root (/) directory (or path you supply)
ls	        List the contents of the present working directory
ls -a	    List all files, including hidden files and directories (those whose name start with .)
tree	    Displays a tree view of the filesystem
```

10. Hard Links
```
The ln utility is used to create hard links and (with the -s option) soft links, also known as symbolic links or symlinks. These two kinds of links are very useful in UNIX-based operating systems.

Suppose that file1 already exists. A hard link, called file2, is created with the command:

$ ln file1 file2

Note that two files now appear to exist. However, a closer inspection of the file listing shows that this is not quite true.

$ ls -li file1 file2

The -i option to ls prints out in the first column the inode number, which is a unique quantity for each file object. This field is the same for both of these files; what is really going on here is that it is only one file, but it has more than one name associated with it, as is indicated by the 2 that appears in the ls output. Thus, there was already another object linked to file1 before the command was executed.
```
11. Soft (Symbolic) Links
Soft (or Symbolic) links are created with the -s option, as in:

$ ln -s file1 file3
$ ls -li file1 file3

Notice file3 no longer appears to be a regular file, and it clearly points to file1 and has a different inode number.
Symbolic links take no extra space on the filesystem (unless their names are very long). They are extremely convenient, as they can easily be modified to point to different places. An easy way to create a shortcut from your home directory to long pathnames is to create a symbolic link.

Unlike hard links, soft links can point to objects even on different filesystems, partitions, and/or disks and other media, which may or may not be currently available or even exist. In the case where the link does not point to a currently available or existing object, you obtain a dangling link.

12. 
```
Navigating Through Directory History
The cd command remembers where you were last, and lets you get back there with cd -. For remembering more than just the last directory visited, use pushd to change the directory instead of cd; this pushes your starting directory onto a list. Using popd will then send you back to those directories, walking in reverse order (the most recent directory will be the first one retrieved with popd). The list of directories is displayed with the dirs command.