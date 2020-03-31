
# Different Aspects of Linux Hardening

## Secure Mounted Filesystems

## Protect /etc/services File

## Remove Unused Accounts

## Hardening Cron Scripts

## Securing SUID Programs

## Risky World-Writable Files and Directories

## Risky Symlinks

## Securing Log Files

## Securing SSH

## sudo Notification

## Securing the Terminal

## Securing Linux Resources

## Hardening /proc Directory

## Restricting the Compilers
The attacker might compile the exploits on his machine and upload it to the victim server without the need to the compilers, but anyway, it’s preferable to restrict the compilers if you don’t use them in production as most modern hosting panels do.

## Awesome Immutable Files (Prevent File Modification)
Immutable files cannot be overwritten by any user, even root. He can’t modify it or delete it unless he removes the immutable bit from it and root user only can do this.

You can say that this feature protects you as root from any mistakes that can damage or harm your system. Awesome!

## Isolating and sandboxing vulnerable software components

## File and Directory Permissions

## Linux Kernel Security Hardening

## Create separated filesystems for /home, /tmp	
Depending on the usage, create a separate filesystem to protect filling up the root filesystem

## System availability
### Configure monitoring	
Monitor system resources and hardware status.
### Disable CTRL-ALT-DEL	
Disable the common combination, to prevent unexpected reboots (e.g. by Windows administrators).
### Create backups and check restores	
Especially after the installation, make sure your backup is working. Check your backups by performing test restores.

## Software
### Remove unneeded software	
Disable and remove unneeded software. Old packages or installations (including PHP based tools) can increase the risk of a succesful break-in.
### Configure automated software patching	
Some distros can automate security patching. While there is a minimal risk of unavailability of a service, it outweighs the risk of security break-ins due to vulnerable software.



[practical-linux-hardening]: https://github.com/trimstray/the-practical-linux-hardening-guide 
[linux-server-hardening-part1]: https://linuxacademy.com/guide/19700-linux-security-and-server-hardening-part1/
[linux-hadrening-bestpractice]: https://likegeeks.com/secure-linux-server-hardening-best-practices/
[linux-hardening-training]: https://www.testandverification.com/wp-content/uploads/tvs-embedded-linux-security-hardening-training.pdf
[linux-security-tricks]: https://likegeeks.com/linux-security-tricks/
[qnx-security-process]: https://www.qnx.com/developers/docs/6.3.0SP3/neutrino/user_guide/security.html
[redhat-7-checklist]: https://security.utexas.edu/os-hardening-checklist/linux-7
[cisofy-checklist]: https://cisofy.com/checklist/linux-security/
[hardening-arch-linux]: https://wiki.archlinux.org/index.php/Security 

# References

- [The Practical Linux Hardening Guide (Github)][practical-linux-hardening]
- [Linux Security And Server Hardening Part-1][linux-server-hardening-part1]
- [Secure Linux Server Using Hardening Best Practices][linux-hadrening-bestpractice]
- [Embedded Linux Security Hardening Training][linux-hardening-training]
- [Useful Linux Security Tricks To Harden Your System][linux-security-tricks]
- [Securing Your System (QNX)][qnx-security-process]
- [RED HAT ENTERPRISE LINUX 7 HARDENING CHECKLIS][redhat-7-checklist]
- [Linux Security Checklist (CISOFY)][cisofy-checklist]
- [Hardening an Arch Linux System][hardening-arch-linux]