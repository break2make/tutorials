
# Objective of (SW/HW) reversing

Read the following links to understand the objectives of revesing:
- 

# Debug symbols

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
