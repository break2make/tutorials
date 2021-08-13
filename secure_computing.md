# Secure computing
We can find these phrases:

- **Trusted computing:** in this case, we assume that hardware platform is trusted but the softwares running on the platfrom does not trust each other. This computing paradigm establish a notion of secure world and non-secure world. While the application running on the secure world has access to the entire platfom, the non-secure world applications has limited access. This isolation is done through physical isolation with the support from the underlying hardware.

- **Confidential computing:** This address the secure computing on an untrusted platform. For example, cloud computing platform is an untrusted platform.

We have different type of computing platforms:
- mobile, IoT device, edge device
- desktop, laptop
- cloud

Note that in case of cloud, the hardware platform is owned and managed by cloud provided, and thus, the computing performned on a cloud platform brings bufferent trust challenge. Ideally, we cannot trust a third part platform owner whihle using the platfom for computations of confidential data. We need to have a different technies to address how to perform a secure computing in an untrusted platform.

# Confidential Computing

Confidential computing is a cloud computing technology that isolates sensitive data in a protected CPU enclave during processing. The contents of the enclave — the data being processed, and the techniques that are used to process it — are accessible only to authorized programming code, and are invisible and unknowable to anything or anyone else, including the cloud provider.

For years, cloud providers have offered encryption services to help protect data `at rest` (in storage and databases) and `data in transit` (moving over a network connection). Confidential computing eliminates the remaining data security vulnerability by protecting data `in use` — that is, during processing or runtime.


Additional resources:
- https://www.ibm.com/cloud/learn/confidential-computing
- 


# AMD Confidential Computing

AMD EPYC processor is extended with the following technilogy as a support for confidential computing:
- Secure encrypted virtualization (SEV) comprises of a secure processor with SEV firmware running on it
- Secure encrypted memory (SEM) controller with embedded ASE encryption enigne 

SEV is used for key management while SEM is used memory encryption and decryption.

To create a secure VM, roughly the following steps are followed:
- Client (Guest owner) send a request to host hypervisor with VM policies and other information and hypervisor also provide this information to SEV to create a guest context
- SEV create a memory encryption key for guest OS
- Hypervisor allocates memory for gesy os and ask SEV to encrypt it 
- Hypervisor loads the guest in the memory and ask SEV to measure it
- Hyperviosor sends the guest os measurement to gest owner
- If the measurement are as expected, the Gest owner send the confidential data to VM over a secure channel

For details of the implementation and API, please chek the AMD official document as given beolow.

For further reading:
- Secure Encrypted Virtualization API Version 0.22 [[pdf](https://developer.amd.com/wp-content/resources/55766.PDF)]
- Trusting in the CPU: Getting to the Roots of Security [[pdf](https://www.amd.com/system/files/2017-06/Trusting-in-the-CPU.pdf)]
- Helping Secure the Cloud with AMD EPYC SEV [[pdf](https://developer.amd.com/wp-content/resources/HelpingSecuretheCloudwithAMDEPYCSEV.pdf)]
- Enarx - Attested, Secured Execution with AMD’s SEV - Nathaniel McCallum & David Kaplan [[video](https://www.youtube.com/watch?v=0-ISmJNxGiY&ab_channel=TheLinuxFoundation)]
- EXTENDING SECURE ENCRYPTED VIRTUALIZATION WITH SEV-ES [[video](https://events19.linuxfoundation.org/wp-content/uploads/2017/12/Extending-Secure-Encrypted-Virtualization-with-SEV-ES-Thomas-Lendacky-AMD.pdf)]
- Exploiting Unprotected I/O Operations in AMD’s Secure Encrypted Virtualization [[paper](https://www.usenix.org/conference/usenixsecurity19/presentation/li-mengyuan)]
