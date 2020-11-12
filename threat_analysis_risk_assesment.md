# Security

Few interesting articles:
- Hardware and Security: Vulnerabilities and Solutions - https://www2.seas.gwu.edu/~simha/research/HWSecBookChapter12.pdf
  Note: this article discuss about to secure a hardware and hardware for software security
- https://www.cybok.org/media/downloads/Hardware_Security_KA_-_draft_for_review_August_2019.pdf
- [Lateral Thinking for Trustworthy Apps](https://os.inf.tu-dresden.de/papers_ps/icdcs2017-lateral-thinking.pdf). Read this to learn how isolation is required for ensuring better software security.


## Threat Analysis

### Book
- Threat Modeling Designing for Security by Adam Shostack. [source](https://moodle.ufsc.br/pluginfile.php/2377555/mod_resource/content/2/Threat%20Modeling.pdf)


## Paper

- TARA+: Controllability-aware Threat Analysis and Risk Assessment for L3 Automated Driving Systems
- An Asset to Security Modeling? Analyzing Stakeholder Collaborations Instead of Threats to Assets
- Threat Modeling for Automotive Security Analysis
- Risk-Oriented Security Engineering (Interesting reading. well-written)
- Combined automotive safety and security pattern engineering approach (Interesting reading)
- [Threat Modeling for Cloud Data Center Infrastructures](https://tsapps.nist.gov/publication/get_pdf.cfm?pub_id=921695)



### Other Resources

- https://medium.com/@informationsecurity/microsoft-threat-modeling-tools-logic-28ea9dd3b18d
- Threat modeling for drivers - https://docs.microsoft.com/en-us/windows-hardware/drivers/driversecurity/threat-modeling-for-drivers
  **Note:** It has used STRDIE model, and this can be used an example for understnading the STRIDE threat modeling. 
- [A Threat-Driven Approach to Cyber Security](https://www.lockheedmartin.com/content/dam/lockheed-martin/rms/documents/cyber/LM-White-Paper-Threat-Driven-Approach.pdf). It contains few examples for attack tree
- [Threat modeling explained: A process for anticipating cyber attacks](https://www.csoonline.com/article/3537370/threat-modeling-explained-a-process-for-anticipating-cyber-attacks.html)
- 



### Tools
- https://github.com/OVVL-HSO/OVVL-Webapp
  - Thesis: https://opus.hs-offenburg.de/frontdoor/deliver/index/docId/3339/file/Bachelorthesis_Tobias_Reski_18.02.2019.pdf
- https://github.com/OVVL-HSO/OVVL-Server
- Microsoft Threat Modeling Tool 2016


## Risk Assessment

Detailed listing of various risk analysis technique can be found [here](https://www.nr.no/~abie/RiskAnalysis.htm).

Risk Analysis Steps:
- Rsik Identification
- Risk Evaluation
- Risk Treatment

### Tools
- securiCAD - https://community.securicad.com/

### Papers
- SAHARA: A Security-Aware Hazard and Risk Analysis Method
- Integrated Safety and Security Risk Assessment Methods: A Survey of Key Characteristics and Applications (has provided a comparison of various techniques)
- https://www.itgovernance.co.uk/blog/7-steps-to-a-successful-iso-27001-risk-assessment
- https://www.enisa.europa.eu/topics/threat-risk-management/risk-management/current-risk/risk-management-inventory/rm-process/risk-treatment
- https://advisera.com/27001academy/blog/2016/05/16/4-mitigation-options-risk-treatment-according-iso-27001/
- https://advisera.com/27001academy/knowledgebase/threats-vulnerabilities/

## Operating System Security

### Windows

-[PMCAP: A Threat Model of Process Memory Data on the Windows Operating System](http://downloads.hindawi.com/journals/scn/2017/4621587.pdf)

### Linux Security

- [Linux Security](https://people.eecs.ku.edu/~saiedian/710/Lectures/Readings/12-linux-security.pdf) Lecture Notes
- [OS-level Attacks and Defenses: From Software to Hardware.](https://tuprints.ulb.tu-darmstadt.de/8482/1/gens_diss.pdf)
- [LINUX AND HYPERVISOR HARDENING — APPLYING A SECURE BY DESIGN PHILOSOPHY.](https://www.starlab.io/blog/linux-and-hypervisor-hardening-applying-a-secure-by-design-philosophy)
- [WINDOWS AND LINUX OPERATING SYSTEMS FROM A SECURITY PERSPECTIVE.](https://arxiv.org/ftp/arxiv/papers/1204/1204.0197.pdf)
- Automating threat modeling using an ontology framework. 
- [Measuring a System’s Attack Surface.](https://www.cs.cmu.edu/~wing/publications/tr04-102.pdf). Note: Read this to understand the attack surfaces in Linux OS. It has also listed various resource in Linux OS.
- [Clear Linux.](https://docs.01.org/clearlinux/latest/guides/index.html#clear-linux). Note: This is a great resource.
- [Operating System Security](https://www.ibr.cs.tu-bs.de/courses/ws1920/oss/index.html). Course at TUB
- [The Security Problem](https://www.cs.uic.edu/~jbell/CourseNotes/OperatingSystems/15_Security.html)



## Application Security

### Well-know security problems

#### Confused deputy problem

>"In information security, the confused deputy problem is often cited as an example of why capability-based security is important. A confused deputy is a legitimate, more privileged computer program that is tricked by another program into misusing its authority on the system. It is a specific type of privilege escalation.
>
>Capability systems protect against the confused deputy problem, whereas access control list-based systems do not." --[wikipedia](https://en.wikipedia.org/wiki/Confused_deputy_problem)

### Resources
- [A Theory and Tools for Applying Sandboxes Effectively](http://www.cs.cmu.edu/~mmaass/pdfs/dissertation.pdf)
- [7 must-dos for delivering app-focused security](https://techbeacon.com/security/7-must-dos-delivering-app-focused-security)
- [10 Steps to Secure Software](https://dzone.com/articles/10-steps-to-secure-software)
- [Capability Theory by Sound Bytes](http://cap-lore.com/CapTheory/)
- [Security of Embedded Software](https://www.diva-portal.org/smash/get/diva2:1149047/FULLTEXT01.pdf)
- [Introduction to Embedded Linux Security - part 1](https://embeddedbits.org/introduction-embedded-linux-security-part-1/)
- [Introduction to Embedded Linux Security - part 2](https://embeddedbits.org/introduction-embedded-linux-security-part-2/)
- https://static.sched.com/hosted_files/ossna2020/72/introduction_embedded_linux_security.pdf
- [Software Security](https://www.cs.colorado.edu/~kena/classes/5828/s12/presentation-materials/stevensonhunteralharbikhali.pdf) By Hunter Stevenson and Khalid Alharbi (Interesting - it has covered the security testing)
- [ISO/IEC 27034:2011+ — Information technology — Security techniques](https://www.iso27001security.com/html/27034.html)
- [Six security tips for embedded systems](https://www.rutronik.com/article/detail/News/six-security-tips-for-embedded-systems/)
- [PaddyFrog: systematically detecting confused deputy vulnerability in Android applications](http://lilicoding.github.io/SA3Repo/papers/2015_wu2015paddyfrog.pdf)
- 


## Automotive Security

- [Security Analysis of Android Automotive](https://rtcl.eecs.umich.edu/rtclweb/assets/publications/2020/mert-sae-2020.pdf)

## Secure IC

### Resources
- [DARPA Doubles Down on Chip-Level Cybersecurity](https://www.allaboutcircuits.com/news/darpa-doubles-down-on-chip-level-cybersecurity/).
  >"DARPA recognizes that hardware security is a specialized discipline mostly dominated by huge merchant semiconductor companies, such as Qualcomm, Intel, and Broadcom. Through 
  >automation, DARPA hopes to democratize the process of building chip-level security, making it an achievable goal for even the smallest of IC builders."
- [Handbook for Robustness Validation of Automotive Electrical/Electronic Modules](https://tinyurl.com/y3qvuz84)
- 

### Papers
- [Opening the Doors to Dynamic Camouflaging: Harnessing the Power of Polymorphic Devices](https://arxiv.org/pdf/1811.06012.pdf)


