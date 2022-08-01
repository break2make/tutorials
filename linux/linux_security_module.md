
# Linux Security Modules (LSM)

This allows many different access control models to be implemented as loadable kernel modules, enabling multiple threads of security policy engine development to proceed independently of the main Linux kernel.

A number of existing enhanced access control implementations, including POSIX.1e capabilities [29], SELinux, Domain and Type Enforcement (DTE) [14] and Linux Intrusion Detection System (LIDS) [17] have already been adapted to use the LSM framework.

Discretionary access controls (root, user-IDs and mode bits) are adequate for user management of their own privacy, **but are not sufficient to protect systems from attack.**

