
## User and Groups

Linux is a multiuser operating system. In a multiuser environment, it is a common administration task to create new users, modify existing users, or remove users. For ease of access management, users are assigned to groups. Creating, deleting, and modifying groups is also another common administration task. [source](https://linuxacademy.com/guide/12659-understanding-linux-users-and-groups/)

**Users**

Users of the system may be human users — people who log into the system or they can be system users — used to start non-interactive background services such as databases. From the perspective of the operating system, there is no distinction between human users and system users and all the information is stored in the same file.

However, there is a range of user IDs reserved for human users and another range for system users.

**Groups**

Groups are a collection of users. Assigning users to groups makes it easier to manage permissions. For example, you can set permissions to ensure that files are accessible to people in a particular group like accounts, hr, etc.

Whenever a user is created, by default, they are added to a new group with the same name as the username. This is called the primary group of the user. A user john would be added to a group named john.

Akin to users, a range of IDs is reserved for regular groups and system groups.

Users and groups are used on GNU/Linux for access control—that is, to control access to the system's files, directories, and peripherals. Linux offers relatively simple/coarse access control mechanisms by default. For more advanced options, see ACL and PAM#Configuration How-Tos. [source](https://wiki.archlinux.org/index.php/Users_and_groups)


### Permissions and ownership
[Source](https://wiki.archlinux.org/index.php/Users_and_groups)  

The UNIX operating system crystallizes a couple of unifying ideas and concepts that shaped its design, user interface, culture and evolution. One of the most important of these is probably the mantra: "everything is a file," widely regarded as one of the defining points of UNIX.
This key design principle consists of providing a unified paradigm for accessing a wide range of input/output resources: documents, directories, hard-drives, CD-ROMs, modems, keyboards, printers, monitors, terminals and even some inter-process and network communications. The trick is to provide a common abstraction for all of these resources, each of which the UNIX fathers called a "file." Since every "file" is exposed through the same API, you can use the same set of basic commands to read/write to a disk, keyboard, document or network device.

*Every file on a GNU/Linux system is owned by a user and a group.* In addition, there are three types of access permissions: read, write, and execute. Different access permissions can be applied to a file's owning user, owning group, and others (those without ownership). One can determine a file's owners and permissions by viewing the long listing format of the ls command.

**Advanced Permissions**
[Source](https://www.linux.com/training-tutorials/understanding-linux-file-permissions/)

The special permissions flag can be marked with any of the following:

_ – no special permissions
d – directory
l– The file or directory is a symbolic link
s – This indicated the setuid/setgid permissions. This is not set displayed in the special permission part of the permissions display, but is represented as a s in the read portion of the owner or group permissions.
t – This indicates the sticky bit permissions. This is not set displayed in the special permission part of the permissions display, but is represented as a t in the executable portion of the all users permissions

**Setuid/Setgid Special Permissions**

The setuid/setguid permissions are used to tell the system to run an executable as the owner with the owner’s permissions.

Be careful using setuid/setgid bits in permissions. If you incorrectly assign permissions to a file owned by root with the setuid/setgid bit set, then you can open your system to intrusion.

You can only assign the setuid/setgid bit by explicitly defining permissions. The character for the setuid/setguid bit is s.

So do set the setuid/setguid bit on file2.sh you would issue the command chmod g+s file2.sh.

**Sticky Bit Special Permissions**

The sticky bit can be very useful in shared environment because when it has been assigned to the permissions on a directory it sets it so only file owner can rename or delete the said file.

You can only assign the sticky bit by explicitly defining permissions. The character for the sticky bit is t.

To set the sticky bit on a directory named dir1 you would issue the command chmod +t dir1.

**When Permissions Are Important**

To some users of Mac- or Windows-based computers you don’t think about permissions, but those environments don’t focus so aggressively on user based rights on files unless you are in a corporate environment. But now you are running a Linux-based system and permission based security is simplified and can be easily used to restrict access as you please.

So I will show you some documents and folders that you want to focus on and show you how the optimal permissions should be set.

- home directories– The users’ home directories are important because you do not want other users to be able to view and modify the files in another user’s documents of desktop. To remedy this you will want the directory to have the drwx______ (700) permissions, so lets say we want to enforce the correct permissions on the user user1’s home directory that can be done by issuing the command chmod 700 /home/user1.

- bootloader configuration files– If you decide to implement password to boot specific operating systems then you will want to remove read and write permissions from the configuration file from all users but root. To do you can change the permissions of the file to 700.

- system and daemon configuration files– It is very important to restrict rights to system and daemon configuration files to restrict users from editing the contents, it may not be advisable to restrict read permissions, but restricting write permissions is a must. In these cases it may be best to modify the rights to 644.

- firewall scripts – It may not always be necessary to block all users from reading the firewall file, but it is advisable to restrict the users from writing to the file. In this case the firewall script is run by the root user automatically on boot, so all other users need no rights, so you can assign the 700 permissions.


**Access Control Lists**

[Source](https://wiki.archlinux.org/index.php/File_permissions_and_attributes)

Access Control Lists provides an additional, more flexible permission mechanism for file systems by allowing to set permissions for any user or group to any file.

**Umask**

The umask utility is used to control the file-creation mode mask, which determines the initial value of file permission bits for newly created files.

**File attributes**

Apart from the file mode bits that control user and group read, write and execute permissions, several file systems support file attributes that enable further customization of allowable file operations. This section describes some of these attributes and how to work with them.

**Resources**
- https://wiki.archlinux.org/index.php/Users_and_groups
- https://www.tutorialspoint.com/unix/unix-file-permission.htm
- https://linuxacademy.com/guide/12659-understanding-linux-users-and-groups/
- https://www.linux.com/training-tutorials/understanding-linux-file-permissions/
- https://wiki.archlinux.org/index.php/File_permissions_and_attributes

## Access Control Mechanisms (ACMs)

It is also known as authorization model.

- https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/5/html/deployment_guide/selg-overview
- [Authorization Models: ACL, DAC, MAC, RBAC, ABAC](https://dinolai.com/notes/others/authorization-models-acl-dac-mac-rbac-abac.html)


## What is Privilege?
According to [Wikipedia](https://en.wikipedia.org/wiki/Privilege_(computing)):

>In computing, privilege is defined as the delegation of authority to perform security-relevant functions on a computer system. A privilege allows a user to perform an action with security consequences. Examples of various privileges include the ability to create a new user, install software, or change kernel functions.
>
>Users who have been delegated extra levels of control are called privileged. Users who lack most privileges are defined as unprivileged, regular, or normal users.

Privileges can either be automatic, granted, or applied for.

An automatic privilege exists when there is no requirement to have permission to perform an action. For example, on systems where people are required to log into a system to use it, logging out will not require a privilege. Systems that do not implement file protection - such as MS-DOS - essentially give unlimited privilege to perform any action on a file.

A granted privilege exists as a result of presenting some credential to the privilege granting authority. This is usually accomplished by logging on to a system with a username and password, and if the username and password supplied are correct, the user is granted additional privileges.

A privilege is applied for by either an executed program issuing a request for advanced privileges, or by running some program to apply for the additional privileges. An example of a user applying for additional privileges is provided by the sudo command to run a command as the root user, or by the Kerberos authentication system.

On Unix-like systems, the superuser (commonly known as 'root') owns all the privileges. Ordinary users are granted only enough permissions to accomplish their most common tasks. UNIX systems have built-in security features. Most users cannot set up a new user account nor do other administrative procedures. The user “root” is a special user, something called super-user, which can do anything at all on the system. This high degree power is necessary to fully administer a UNIX system, but it also allows its user to make a mistake and cause system problems.

## Principle of least privilege
https://dwheeler.com/secure-programs/Secure-Programs-HOWTO/minimize-privileges.html



# Single User Mode



# Uboot

Important readings:
- Porting U-Boot and Linux on new ARM boards: a step-by-step guide [[video](https://www.youtube.com/watch?v=5E0sdYkvq-Q)|[slide](https://elinux.org/images/2/2a/Schulz-how-to-support-new-board-u-boot-linux.pdf)]
- Build U-Boot and Linux Kernel from Source Code [[Link](https://developer.toradex.com/knowledge-base/build-u-boot-and-linux-kernel-from-source-code#imx88x8mm)]
- U-Boot programming [[link](http://xillybus.com/tutorials/uboot-hacking-howto-1)]
- U-boot from scratch [[link](https://www.youtube.com/watch?v=To9LKF4Iwgw)]

# Device Tree

Important readings:
- Device Tree for Dummies! - Thomas Petazzoni, Free Electrons [[video](https://www.youtube.com/watch?v=m_NyYEBxfn8)|[slide](https://elinux.org/images/f/f9/Petazzoni-device-tree-dummies_0.pdf)]

# Kernel

# Kernel Data Structure



# Other resources
- Exploring Linux Kernel Source Code with Eclipse and QTCreator [[video](https://www.youtube.com/watch?v=0CGRkXIUM-o)]
- Building the Simplest Possible Linux System [[video](https://www.youtube.com/watch?v=Sk9TatW9ino)]
- Kernel basics [[video](https://www.youtube.com/watch?v=rTcnTOXf_jM)]
- Embedded Linux Booting Process (Multi-Stage Bootloaders, Kernel, Filesystem) [[video](https://www.youtube.com/watch?v=DV5S_ZSdK0s)]
- U-Boot [[link](https://linux-sunxi.org/U-Boot)]
- Analyzing the Linux boot process [[link](https://opensource.com/article/18/1/analyzing-linux-boot-process)]
