
# ARM TrustZone

![](https://www.researchgate.net/profile/Zhenyu-Ning/publication/328228513/figure/fig2/AS:686400684949505@1540662084927/ARM-TrustZone-Technology.png)

![](https://linuxgizmos.com/files/arm-trustzone-architecture.jpg)


![](https://documentation-service.arm.com/static/5efa1a5ddbdee951c1ccdeba?token=)

![](https://www.sierraware.com/sierrateesoftwarearchitecture.png)

![](https://www.mdpi.com/electronics/electronics-09-01130/article_deploy/html/images/electronics-09-01130-g001.png)

![](https://www.mdpi.com/electronics/electronics-09-01130/article_deploy/html/images/electronics-09-01130-g005.png)

![](https://www.cpsec.aist.go.jp/team/cprt/research/research04/r04-01e.png)

![](https://linuxgizmos.com/files/linaro_optee_arch.jpg)

![](https://bootlin.com/pub/conferences/2021/elc/leger-optee-linux-interaction/src/graphics/op-tee-software-architecture.jpg)

![](https://projectacrn.github.io/1.6.1/_images/trustyacrn-image1.png)

![](https://sunlab-gmu.github.io/research/img/rustee_arch.png)

![](https://community.arm.com/resized-image/__size/1040x0/__key/communityserver-blogs-components-weblogfiles/00-00-00-21-42/6574.TrustZone-for-ARMv8_2D00_M-_2D00_-Security-for-all-embedded-applications.png)

## System/Hardware architecture

![](https://www.researchgate.net/profile/Steffen-Schulz-7/publication/264124588/figure/fig4/AS:295827667996701@1447542220928/Overview-of-the-ARM-TrustZone-system-architecture-9.png)

**ARM TrustZOne System architecture.**

![](https://www.mdpi.com/electronics/electronics-09-01130/article_deploy/html/images/electronics-09-01130-g001-550.jpg)

**Architecture on a TrustZone-assisted System-On-Chip (SoC)**

![](https://www.researchgate.net/publication/325532896/figure/fig1/AS:961406342017024@1606228542296/Structure-of-TEE-based-on-ARM-TrustZone-hardware_Q640.jpg)

![](https://genode.org/documentation/articles/tz_two_worlds.png)


![](https://soclabs.org/sites/default/files/styles/large/public/2021-08/TZC.JPG?itok=gkmnSgq3)

![](image/i26pmg1.png)

![](https://projectacrn.github.io/1.6.1/_images/trustyacrn-image1.png)


## Context switching (Trasition between secure and non-secure worlds)

As mentioned previously, the primary role of the monitor is to context switch resources that are needed in both worlds. Any secure state saved by the monitor should be saved into a region of Secure memory, so that the Normal world cannot tamper with it.

Exactly what needs to be saved and restored for each switch depends on the hardware design, and the software model used for inter-world communications. The list typically includes:

All general purpose ARM registers.
Any coprocessor registers, such as NEON or VFP. Note: Only required if coprocessor is used in both worlds.
Any world-dependant processor configuration state in CP15.

Links:
- Context switching



## Links
- https://microchipdeveloper.com/32arm:saml11-trustzone-implementation
- [MiniTEE—A Lightweight TrustZone-Assisted TEE for Real-Time Systems](https://www.mdpi.com/2079-9292/9/7/1130/htm)
- [Secure Initialization of TEEs - when secure boot falls short…](https://www.riscure.com/uploads/2017/08/euskalhack_2017_-_secure_initialization_of_tees_when_secure_boot_falls_short.pdf)
- [How the Secure model works](https://developer.arm.com/documentation/ddi0333/h/programmer-s-model/secure-world-and-non-secure-world-operation-with-trustzone/how-the-secure-model-works)




# Others

![](https://blog.techdesign.com/wp-content/uploads/2020/06/Intel-SGX-and-AMD-SEV-operating-concepts.png)