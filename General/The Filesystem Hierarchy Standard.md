/

The root of the entire filesystem tree. Every file and directory on the system lives beneath this point. This is roughly equivalent to C:\ on Windows, though unlike Windows, Linux does not use drive letters.

/home

Personal directories for each user (e.g., /home/student). This is equivalent to C:\Users\ on Windows and /Users/ on macOS.

/root

The home directory for the system's superuser. It is kept separate from /home for security reasons. Windows and macOS have no direct equivalent.

/etc

System-wide configuration files. If an application needs a settings file that affects all users, it lives here. macOS uses the same name, but it is a symbolic link to /private/etc. Windows stores equivalent settings in the registry and C:\Windows\System32\.

/bin and /usr/bin 

Essential user-facing programs and commands (e.g., ls, cp, bash). On most modern distributions, /bin is a symbolic link to /usr/bin. Roughly equivalent to C:\Windows\System32\ on Windows. macOS uses the same directory names.

/sbin and /usr/sbin

System administration programs intended for use by the root user. macOS uses the same directory names. Windows stores equivalent utilities in C:\Windows\System32\.

/lib and /usr/lib

Shared libraries required by programs in /bin and /sbin. Equivalent to .dll files in C:\Windows\System32\ on Windows. macOS uses /usr/lib for the same purpose.

/var

Variable data that changes during normal operation, such as log files (/var/log), print queues, and mail spools. macOS uses the same name, implemented as a symbolic link to /private/var. Windows spreads equivalent data across C:\Windows\ and C:\ProgramData\.

/tmp

Temporary files created by applications. These are not guaranteed to survive a reboot. Equivalent to C:\Windows\Temp\ on Windows. macOS uses the same name, implemented as a symbolic link to /private/tmp.

/dev

Device files. Linux represents hardware (hard drives, terminals, USB devices) as files in this directory. macOS follows the same convention. Windows handles device access through the Device Manager and kernel drivers, with no user-visible equivalent.

/proc

A virtual filesystem that exposes real-time information about running processes and the kernel. Nothing here is stored on disk; it is generated on demand. Neither Windows nor macOS have a direct equivalent.

/sys

A virtual filesystem providing a structured interface to kernel and hardware information. Neither Windows nor macOS have a direct equivalent.

/boot

Files required to start the system, including the Linux kernel itself. Windows manages boot files through the Windows Boot Manager; macOS handles booting through its own firmware. Neither exposes these files in a user-navigable folder in the same way.

/run

Runtime data for processes started since the last boot, such as process ID files and lock files. Neither Windows nor macOS have a direct equivalent.


# Key Subdirectories of /usr

Directory

Contains

/usr/bin

The vast majority of user-facing commands and programs.

/usr/sbin

System administration tools not required at boot.

/usr/lib

Shared libraries for programs in /usr/bin and /usr/sbin.

/usr/share

Architecture-independent data such as documentation and icons.

/usr/local 

Software installed manually by the system administrator, outside the distribution's package manager.


On most modern Linux distributions, the distinction between /bin and /usr/bin (and their counterparts) has been removed entirely: /bin is simply a symbolic link pointing to /usr/bin. This change reflects the reality that the original reason for the separation (fitting the system onto multiple smaller disks) no longer applies to modern hardware. You may still encounter both paths in documentation and scripts, but they lead to the same place on current systems.

The key takeaway is that when you are looking for a program or tool on a Linux system, /usr/bin is the first place to look. If you have installed software manually or compiled something from source, check /usr/local/bin.