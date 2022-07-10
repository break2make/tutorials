
![](https://www.microcontrollertips.com/wp-content/uploads/2021/04/Open-Source-Vs-Commercial-RISC-V-Licensing-Models.png)

**Commercial vs. open-source IP licensing models. (Image: RISC-V International)**
Links:
- https://www.microcontrollertips.com/risc-v-vs-arm-vs-x86-whats-the-difference/
- 


# CPU Priveldege Levels

## Why do we even think about CPU priveledge levels?

Modern software expects to be split into different modules, each with a different level of access to system and processor resources. An example of this is the split between the operating system kernel, which has a high level of access to system resources, and user applications, which have a more limited ability to configure the system. 

Most software developers are at least somewhat familiar with the concept of privilege on a computer. For example, the operating system is able to perform operations that are prohibited for processes running in user space. This allows for isolation and protection; a single process is not able to access the memory of another, and a process that crashes does not corrupt the entire system. To enable this model, hardware must offer varying levels of privilege and the ability to move between them.

## What is the protection ring for linux operating system?

## How the Privilege Rings Interact?
- https://www.makeuseof.com/what-are-cpu-protection-privilege-rings/


## What are the ARM privilege/exception levels?

![](blob:https://developer.arm.com/f9cbb1f2-cfb6-4992-8733-47dbdd914e45)
**Exception levels are referred to as EL<x>**

>Note: The architecture does not enforce this software model, but standard software assumes this model.

Links:
- https://developer.arm.com/documentation/102412/0100/Privilege-and-Exception-levels
- [Mode, state, and privilege level](https://developer.arm.com/documentation/ddi0406/cb/System-Level-Architecture/The-System-Level-Programmers--Model/System-level-concepts-and-terminology/Mode--state--and-privilege-level?lang=en)
- [Understanding Access Levels – ARM Cortex-M](https://www.iotality.com/armcm-access-levels/)

## What are the x86 privilege levels?

![](https://upload.wikimedia.org/wikipedia/commons/thumb/2/2f/Priv_rings.svg/1280px-Priv_rings.svg.png)
**Privilege rings for the x86 available in protected mode**

Links:
- https://en.wikipedia.org/wiki/Protection_ring

## What are the RISC-V privilege levels?

RISC-V has three software privilege levels (in increasing order of capability): user-mode (U-mode), supervisor mode (S-mode), and machine mode (M-mode). The processor can run in only one of the privilege modes at a time.

Privilege level defines what the running software can do during its execution. Common usage of each privilege level is as follows:
- U-mode: user processes
- S-mode: kernel (including kernel modules and device drivers), hypervisor
- M-mode: bootloader, firmware

> RISC-V also defines hypervisor priviliege mode (H-mode), but the spec of H-mode is not included in the stable revision (RISC-V Priv. v1.10).

![](https://danielmangum.com/static/risc_v_priv_levels_1.png)
**RISC-V Privilege Levels**

Links
- [RISC-V Privilieged ISA](http://docs.keystone-enclave.org/en/latest/Getting-Started/How-Keystone-Works/RISC-V-Background.html#:~:text=RISC%2DV%20has%20three%20software,privilege%20modes%20at%20a%20time.)
- [RISC-V BYTES: PRIVILEGE LEVELS](https://danielmangum.com/posts/risc-v-bytes-privilege-levels/) Must read
- 

