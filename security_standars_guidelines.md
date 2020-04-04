
# Protection Profiles

According to [Wikipedia](https://en.wikipedia.org/wiki/Protection_Profile):
>A Protection Profile (PP) is a document used as part of the certification process according to ISO/IEC 15408 and the Common Criteria (CC). As the generic form of a Security Target (ST), it is typically created by a user or user community and provides an implementation independent specification of information assurance security requirements. A PP is a combination of threats, security objectives, assumptions, security functional requirements (SFRs), security assurance requirements (SARs) and rationales.
>
>A PP specifies generic security evaluation criteria to substantiate vendors' claims of a given family of information system products. Among others, it typically specifies the Evaluation Assurance Level (EAL), a number 1 through 7, indicating the depth and rigor of the security evaluation, usually in the form of supporting documentation and testing, that a product meets the security requirements specified in the PP.


## Common Criteria Protection Profiles

As a part of Common Criteria, there are many [protection profiles](https://www.commoncriteriaportal.org/pps/) for the following aspects of a system:
- Access Control Devices and Systems
- Biometric Systems and Devices
- Boundary Protection Devices and Systems
- Data Protection
    - Firewall Protection Profile
- Databases
- ICs, Smart Cards and Smart Card-Related Devices and Systems
- Key Management Systems
    - Certificate Issuing and Management Components Protection Profile 
- Mobility
- Multi-Function Devices
- Network and Network-Related Devices and Systems
- Operating Systems
    - Protection Profile for General Purpose Operating Systems, Version 4.2.1
    - Operating System Protection Profile, Version 2.0
- Other Devices and Systems
- Products for Digital Signatures
- Trusted Computing

Understanding of these protection profiles help to make a system secure. 
> Operating System Protection profile is important for securing OS and its auidt.

## Resources
- https://www.commoncriteriaportal.org/pps/
- https://www.niap-ccevs.org/Profile/PP.cfm
- https://www.sogis.eu/uk/pp_en.html
- https://public.cyber.mil/stigs/niap/
- https://www.sciencedirect.com/topics/computer-science/protection-profile


# OpenSCAP Security Guide
The SCAP Security Guide Project: https://www.open-scap.org/security-policies/scap-security-guide.
This guide presents a catalog of security-relevant configuration settings for `Red Hat Enterprise Linux 8` using the following profiles:
- Criminal Justice Information Services (CJIS) Security Policy
- Unclassified Information in Non-federal Information Systems and Organizations (NIST 800-171)
- Australian Cyber Security Centre (ACSC) Essential Eight
- Health Insurance Portability and Accountability Act (HIPAA)
- Protection Profile for General Purpose Operating Systems
- Protection Profile for Virtualization (VPP) v. 1.0
- DISA STIG for Red Hat Enterprise Linux Virtualization Host (RHELH)
- PCI-DSS v3.2.1 Control Baseline
- Red Hat Corporate Profile for Certified Cloud Providers (RH CCP)
- Standard System Security Profile for Red Hat Enterprise Linux 8
-  DISA STIG for Red Hat Enterprise Linux 8

> Although most of the profiles are applicable for [Linux OS distributions][static-open-scap], it can also be used for Unix-like OS with certain modifications.


[static-open-scap]: https://static.open-scap.org/
## Resources
- https://static.open-scap.org/
- https://nvd.nist.gov/ncp/checklist/909/download/5619
- https://nvd.nist.gov/ncp/repository

# SAE International
It is previously known as the Society of Automotive Engineers. Website: https://www.sae.org/\
All SAE publication can be found in [SAE Mobilus](https://saemobilus.sae.org/).

### Selected publications
- [Securing the Modern Vehicle: A Study of Automotive Industry Cybersecurity Practices](https://www.sae.org/binaries/content/assets/cm/content/topics/cybersecurity/securing_the_modern_vehicle.pdf)
- [Hardware Protected Security for Ground Vehicles (Ground Vehicle Standard J3101)](https://saemobilus.sae.org/content/J3101_202002/)
- [Leveraging Hardware Security to Secure Connected Vehicles](https://saemobilus.sae.org/content/2018-01-0012/)
- [Case Study for Defining Security Goals and Requirements for Automotive Security Parts Using Threat Modeling](https://saemobilus.sae.org/content/2018-01-0014/)


# United Nations Economic Commission for Europe (UNECE)

World Forum for Harmonization of Vehicle Regulations (`WP 29`) offers a unique framework for globally harmonized regulations on vehicles. The benefits of such harmonized regulations are tangible in road safety, environmental protection and trade. More details can be found [here](http://www.unece.org/trans/main/welcwp29.html)

### ECE/TRANS/WP.29/GRVA/2019/3 
(TF on Cyber Security and Over-the-air issues) Draft Recommendation on Software Updates of the Task Force on Cyber Security and Over-the-air issues. [Link](https://www.unece.org/trans/main/wp29/wp29wgs/wp29grva/grva2019.html)

### ECE/TRANS/WP.29/GRVA/2019/2 
(TF on Cyber Security and Over-the-air issues) Proposal for a Recommendation on Cyber Security. [Link](https://www.unece.org/trans/main/wp29/wp29wgs/wp29grva/grva2019.html)


**Other Links**:
- https://www.unece.org/trans/main/wp29/wp29wgs/wp29grva/grvainf2019.html
- https://www.unece.org/trans/main/wp29/wp29wgs/wp29grva/grva2019.html

# European Union Agency for Cybersecurity (ENISA) 
Website: https://www.enisa.europa.eu/ \
All publication can be find [here](https://www.enisa.europa.eu/publications#c5=2010&c5=2020&c5=false&c2=publicationDate&reversed=on&b_start=0).

### Selected publications:
- [Cyber Security and Resilience of smart cars](https://www.enisa.europa.eu/publications/cyber-security-and-resilience-of-smart-cars)
- [ENISA good practices for security of Smart Cars](https://www.enisa.europa.eu/publications/smart-cars)
- [Good Practices for Security of IoT - Secure Software Development Lifecycle](https://www.enisa.europa.eu/publications/good-practices-for-security-of-iot-1)