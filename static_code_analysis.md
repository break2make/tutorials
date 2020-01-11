**Secure coding** is a coding practice which guides how to avoid the coding flaws that might be exploited by attackers to violet different security goals. Note that there might be different ways to write a secure code, and thus, secure coding guideline usually talks about what to avoid, not how to avoid. _Programming languages provide different libraries for secure code development, which shall be used instead of its insecure variants._

**Secure static code analysis** is a static code analysis technique to ensure the conformance of secure coding rules. This can be done manually or using tools. However, don't believe on the output of signle secure code analysis tool as most of the case, tools report many false positive cases. _If you are a security personnel and supporting a development team, it should be your responsibility to eliminet those false positive cases, and share only the real issues with the development team. Otherwise, the developers will be overwhelmed with the issues which distract their focus and will be less interested in correcting those._  

# Top 10 secure coding practice

_Source: https://wiki.sei.cmu.edu/confluence/display/seccode/Top+10+Secure+Coding+Practices_

- **Validate input.** Validate input from all untrusted data sources. Be suspicious of most external data sources, including command line arguments, network interfaces, environmental variables, and user controlled files.
- **Heed compiler warnings.** Compile code using the highest warning level available for your compiler and eliminate warnings by modifying the code. Use static and dynamic analysis tools to detect and eliminate additional security flaws.
- **Architect and design for security policies.** Create a software architecture and design your software to implement and enforce security policies. For example, if your system requires different privileges at different times, consider dividing the system into distinct intercommunicating subsystems, each with an appropriate privilege set.
- **Keep it simple.** Keep the design as simple and small as possibl. Complex designs increase the likelihood that errors will be made in their implementation, configuration, and use. Additionally, the effort required to achieve an appropriate level of assurance increases dramatically as security mechanisms become more complex.
- **Default deny.** Base access decisions on permission rather than exclusion. This means that, by default, access is denied and the protection scheme identifies conditions under which access is permitted.
- **Adhere to the principle of least privilege.** Every process should execute with the the least set of privileges necessary to complete the job. Any elevated permission should only be accessed for the least amount of time required to complete the privileged task. This approach reduces the opportunities an attacker has to execute arbitrary code with elevated privileges.
- **Sanitize data sent to other systems.** Sanitize all data passed to complex subsystems such as command shells, relational databases, and commercial off-the-shelf (COTS) components. Attackers may be able to invoke unused functionality in these components through the use of SQL, command, or other injection attacks. This is not necessarily an input validation problem because the complex subsystem being invoked does not understand the context in which the call is made. Because the calling process understands the context, it is responsible for sanitizing the data before invoking the subsystem.
- **Practice defense in depth.** Manage risk with multiple defensive strategies, so that if one layer of defense turns out to be inadequate, another layer of defense can prevent a security flaw from becoming an exploitable vulnerability and/or limit the consequences of a successful exploit. For example, combining secure programming techniques with secure runtime environments should reduce the likelihood that vulnerabilities remaining in the code at deployment time can be exploited in the operational environment.
- **Use effective quality assurance techniques.** Good quality assurance techniques can be effective in identifying and eliminating vulnerabilities. Fuzz testing, penetration testing, and source code audits should all be incorporated as part of an effective quality assurance program. Independent security reviews can lead to more secure systems. External reviewers bring an independent perspective; for example, in identifying and correcting invalid assumptions.
- **Adopt a secure coding standard.** Develop and/or apply a secure coding standard for your target development language and platform.

# SEI CERT

SEI CERT has prepared a set of rules and recommendations for secure coding in different languages like C, C++, Java and Perl. If you are interested, visit their confluence wiki which is having all latest rules and recommendations: https://wiki.sei.cmu.edu/confluence/display/seccode

In additition, they have introduced a new tool SCALe (Source Code Analysis Laboratory), to aduit the outputs of different opensource and commercial code analysis tools. According to them, it will help you identify the false positive cases efficiently. Go through the following links to know more about it:
- https://insights.sei.cmu.edu/sei_blog/2018/09/scale-a-tool-for-managing-output-from-static-code-analyzers.html
- https://github.com/cmu-sei/SCALe

