


# Handling File Operations

Copying from: https://www.quora.com/What-is-the-difference-between-the-OS-module-and-the-shutil-module-in-Python

os is largely thin wrappers around POSIX system calls and library functions, or emulations thereof on some platforms. You’ll find almost identically-named functions in C and other languages, that perform analogously. The magic constants like os.R_OK, os.WNOHANG, etc are named exactly after the C/POSIX values and have the same value as them.

shutil contains high-level Python-specific functions. These are built on top of Python’s os module and each call may represent dozens or hundreds of calls to lower-level functions.

- shutil — High-level file operations
  - https://automatetheboringstuff.com/chapter9/
  - https://stackoverflow.com/questions/12990112/how-to-remove-folder-in-python-rmtree-onerror
- https://pypi.org/project/pyfastcopy/



# Figlet using python package



# Threading and multiprocessing

## The method join()
>join([timeout]) Wait until the thread terminates. This blocks the calling thread until the thread whose join() method is called terminates – either normally or through an unhandled exception – or until the optional timeout occurs.

I found a nice ASCII-art (source: https://stackoverflow.com/questions/15085348/what-is-the-use-of-join-in-python-threading) which explains the behaviours of parent and child in a precise manner. The following text is copied from the source mentioned above.

join-calling should be placed in the track of the main-thread, but to express thread-relation and keep it as simple as possible, I choose to place it in the child-thread instead.

```
without join:
+---+---+------------------                     main-thread
    |   |
    |   +...........                            child-thread(short)
    +..................................         child-thread(long)

with join
+---+---+------------------***********+###      main-thread
    |   |                             |
    |   +...........join()            |         child-thread(short)
    +......................join()......         child-thread(long)

with join and daemon thread
+-+--+---+------------------***********+###     parent-thread
  |  |   |                             |
  |  |   +...........join()            |        child-thread(short)
  |  +......................join()......        child-thread(long)
  +,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,     child-thread(long + daemonized)

'-' main-thread/parent-thread/main-program execution
'.' child-thread execution
'#' optional parent-thread execution after join()-blocked parent-thread could 
    continue
'*' main-thread 'sleeping' in join-method, waiting for child-thread to finish
',' daemonized thread - 'ignores' lifetime of other threads;
    terminates when main-programs exits; is normally meant for 
    join-independent tasks
```

If, for example, you want to concurrently download a bunch of pages to concatenate them into a single large page, you may start concurrent downloads using threads, but need to wait until the last page/thread is finished before you start assembling a single page out of many. That's when you use join().

## Links
[1] https://www.devdungeon.com/content/create-ascii-art-text-banners-python
