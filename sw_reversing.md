# Software Reversing

Three broad objectives of reverengineering are (as mentioned in https://www.thesoftwareguild.com/blog/what-is-reverse-engineering/)
- **Product and Process Improvement** \
Many software developers use reverse engineering to improve their own code or to improve interoperability between programs. Many software suites have application programming interfaces (APIs) that allow for interoperability. “But experts say most APIs are so poorly written that third-party software makers have little choice but to reverse-engineer the programs with which they want their software to work opens in new window, just to ensure compatibility,” according to Mathew Schwartz of Computerworld.\
Schwartz goes on to describe how Cyrix Corp. and Advanced Micro Devices Inc. managed to reverse-engineer Intel’s microprocessors to bring a less expensive, competitive product to market. While operating systems are usually too large and complex to reverse-engineer, “applications are ripe for reverse-engineering.”

- **Cybersecurity** \
Reverse-engineering viruses and other malware is common practice for companies that develop security software. According to a study by Zeltser Security Corp, “repeatable forensics steps should assist members of the defense community in developing a structured approach to understanding inner-workings of malicious software opens in new window.” By taking a piece of malware apart and studying it, a cybersecurity company can develop tools to combat the techniques used by malware developers, rather than reactively developing defenses for individual malware programs.\
Reverse engineering is also used to find security flaws in software, Schwartz says. Though some companies use this to create defenses against such security flaws, hackers who create malicious software can use this process to find gaps in security that they can exploit.

- **Intelligence and Espionage** \
Cyber warfare is becoming an increasingly important threat to guard against; in 2014 alone, the U.S. government suffered 61,000 cybersecurity breaches opens in new window, according to Time. In fact, the Economic Espionage Act of 1996 specifically addresses reverse engineering opens in new windowand its legality and uses. As countries become more reliant on computer systems for warfare, commerce and more, they become increasingly vulnerable to those who reverse-engineer systems to find security holes to exploit.

Specific to security, objectives of reversing binaries can be one or more the followings:
- Discover vulnerabilities
- entify how a process works, such as an authentication method
- cument existing proprietary network protocols or file formats
- ther necessary information for other testing techniques, such as fuzzing
- Trace the use and storage of sensitive information, such as accounts, certificates, encryption keys

There are two approaches: static and dynamic reverse-engineering methods. A static reverse engineering comprises of disassembling binaries, reviewing directory structures and files. By contrast, a dynamic reverse engineering is performed while the target is executing. This allows to leverage the target’s runtime behavior during our analysis. The runtime behaviors tell what type of resources are used, such as files, network requests, and shared objects, and allows to trace the execution flow and track the functions that are in use.

Read the following links to understand the objectives of revesing: 
- https://ioactive.com/service/full-stack-security-assessments/reverse-engineering/
- https://www.thesoftwareguild.com/blog/what-is-reverse-engineering/
- https://teambi0s.gitlab.io/bi0s-wiki/reversing/intro/
- https://ieeexplore.ieee.org/abstract/document/7975746
- https://www.cs.drexel.edu/~spiros/teaching/CS675/slides/intro-binary-reversing.pdf
- https://link.springer.com/chapter/10.1007/978-3-642-04117-4_31



## Debug symbols

Read the following links:
- https://en.wikipedia.org/wiki/Debug_symbol

## Tools
### strip
- https://www.technovelty.org/linux/stripping-shared-libraries.html
- https://www.computerhope.com/unix/strip.htm
- https://stackoverflow.com/questions/1349166/what-is-the-difference-between-gcc-s-and-a-strip-command

### file

File command is used to determine the type of a file. .file type may be of human-readable(e.g. ‘ASCII text’) or MIME type(e.g. ‘text/plain; charset=us-ascii’). This command tests each argument in an attempt to categorize it.

It has three sets of tests as follows:

filesystem test: This test is based on the result which returns from a stat system call. The program verifies that if the file is empty, or if it’s some sort of special file. This test causes the file type to be printed.
magic test: These tests are used to check for files with data in particular fixed formats.
language test: This test search for particular strings which can appear anywhere in the first few blocks of a file.

- https://www.geeksforgeeks.org/file-command-in-linux-with-examples/

### srec_cat
The simplest of the things srec_cat can do is convert from one EPROM file format to another. Please keep in mind, as you read this section, that you can do many of these things simultaneously in one command. They are only broken out separately to make them easier to understand.

If supports many features as mentioned in https://linux.die.net/man/1/srec_examples

### Intelhex

- https://github.com/python-intelhex/intelhex


### Hex editors

- https://www.poftut.com/best-linux-hex-editors/
- https://www.ubuntupit.com/best-linux-hex-editor-top-20-linux-hex-viewers-editors/
- https://stackoverflow.com/questions/5498197/need-a-good-hex-editor-for-linux
