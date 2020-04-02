
# JTAG as Attack Vector

JTAG supports various functions, such as 
- debugging for both hardware and software, 
- downloading firmware, and
- testing a chip device. 

In addition, it is possible to be used for verifying errors by fault 
injection and collecting the device’s internal data from the forensic point 
of view. In spite of these beneficial purposes, there are dysfunctional problems 
that an attacker, who is not a legitimate user, utilizes as a malicious
tool. 

JTAG access may bestow at least the following privileges:
- Reading and writing from system memory
- Pausing execution of firmware (by setting breakpoints)
- Patching instructions or data in memory
- Injecting instructions directly into the pipeline of the target chip (without modifying memory)
- Extracting firmware (for reverse engineering/vulnerability research)
- Executing private instructions to activate other engines within the chip


This kind of attack can be malicious, for instance causing system corruption, 
exposure of encryption/decryption keys and execution codes, insertion of
malicious function, and cloning of the system. Therefore, in
order to counteract such threats, various techniques are proposed to enhance 
security at the hardware and software levels as mentioned [here][jtag-sec].


[jtag-sec]: https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7794515

## Important reading:

- [Rooting a router through JTAG](https://blog.senr.io/blog/jtag-explained)
- [5 Things to Do Now: the USB/JTAG/IME Exploit](https://ci.security/resources/news/article/5-things-to-do-now-the-usb-jtag-ime-exploit)
- [Locks, Keys and Traps Securing Device Jtag Interfaces](https://blog.asset-intertech.com/test_data_out/2017/07/locks-keys-and-traps-securing-device-jtag-interfaces.html)
- [IC Protection Against JTAG-Based Attacks](https://ieeexplore.ieee.org/document/8281506)
- [IoT Security: Firmware Dump](https://www.lufsec.com/iot-security-firmware-dump/)
- [IoT Security: Starting with JTAG hacking](https://www.lufsec.com/iot-security-starting-with-jtag-hacking/)
- [A Brief Review on JTAG Security](jtag-sec)
- [Attacks and Defenses for JTAG](https://pdfs.semanticscholar.org/3e54/49fecc962cd750acfe47b3ddf6c23ccaf2e7.pdf)
- [JTAG 101 – Part 1: Overview and On-Chip Debug Methods](https://www.eetimes.com/jtag-101-part-1-overview-and-on-chip-debug-methods/)
- [Debugging with JTAG](https://elinux.org/images/5/56/DebuggingWithJtagCelf2009.pdf)
- [JTAG Technical Primer](https://www.corelis.com/education/tutorials/jtag-tutorial/jtag-technical-primer/)
- [JTAG TAP Controller Tutorial (video)](https://www.youtube.com/watch?v=PhaqHKyAvR4)
- [EEVblog #499 - What is JTAG and Boundary Scan? (video)](https://www.youtube.com/watch?v=TlWlLeC5BUs&t=1547s)
- [JTAG | IJTAG Semiconductor and Board Test Security](https://www.asset-intertech.com/eresources/jtag-ijtag-semiconductor-and-board-test-security)