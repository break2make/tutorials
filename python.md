


# Handling File Operations

Copying from: https://www.quora.com/What-is-the-difference-between-the-OS-module-and-the-shutil-module-in-Python

os is largely thin wrappers around POSIX system calls and library functions, or emulations thereof on some platforms. You’ll find almost identically-named functions in C and other languages, that perform analogously. The magic constants like os.R_OK, os.WNOHANG, etc are named exactly after the C/POSIX values and have the same value as them.

shutil contains high-level Python-specific functions. These are built on top of Python’s os module and each call may represent dozens or hundreds of calls to lower-level functions.

- shutil — High-level file operations
  - https://automatetheboringstuff.com/chapter9/
- https://pypi.org/project/pyfastcopy/



# Figlet using python package


## Links
[1] https://www.devdungeon.com/content/create-ascii-art-text-banners-python
