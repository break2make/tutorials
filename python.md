# Global Variable
Source: http://net-informations.com/python/iq/global.htm

A global variable is a variable which is accessible in multiple scopes. In Python, it is better to use a single module to hold all the global variables you want to use and whenever you want to use them, just import this module, and then you can modify that and it will be visible in other modules that do the same.

Create a Global module
``` 
#global.py
current_value=0
```

Create a Python program file to access global variable

```
#updater.py
import global
def update_value():
  global.current_value = 100
```

Create another Python program to test value is changed or not

```
#display_value.py
import global
import updater
updater.update_value()
print(global.current_value)
```

Using global variables in a function
A global can be accessed by any function , but it can only be modified if you explicitly declare it with the 'global' keyword inside the function. To use global variables inside a function, you need to do global < varName > inside the function. Keep in mind, that you only need to declare them global inside the function if you want to do assignments / change them. global is not needed for printing and accessing.

example
``` 
myGlobal = 5
def func1():
    myGlobal = 50
def func2():
    global myGlobal
    myGlobal = 50
def func3():
    print (myGlobal)
func1()
func3()
print("After using Global")
func2()
func3()

output
 
5
After using Global
50
```



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

## Important reading
- https://docs.python.org/2.7/library/multiprocessing.html#all-platforms
- https://www.journaldev.com/15631/python-multiprocessing-example
- https://www.tutorialspoint.com/concurrency_in_python/concurrency_in_python_multiprocessing.htm
- https://www.geeksforgeeks.org/python-different-ways-to-kill-a-thread/
- https://pymotw.com/2/multiprocessing/basics.html
- https://www.bogotobogo.com/python/Multithread/python_multithreading_subclassing_creating_threads.php
- https://www.toptal.com/python/beginners-guide-to-concurrency-and-parallelism-in-python

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
