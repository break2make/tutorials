


# Links
- Correctness Testing of Loop Optimizations in C and C++ Compilers [[Pdf](https://solidsands.com/wp-content/uploads/thesis_remi_van_veen.pdf)]



# Tricks
- C++ Tricks - Argument Packing, Macros and Templates [[video](https://www.youtube.com/watch?v=7qZ2O5-uLO8)]
- How to Adopt Modern C++17 into Your C++ Code : Build 2018 [[video](https://www.youtube.com/watch?v=UsrHQAzSXkA)]


# C++ 11 Features

- The 15 C++11 features you must really use in your C++ projects [[link](https://cppdepend.com/blog/?p=319)]
- Move semantics [[pdf](https://www.stroustrup.com/move.pdf)]
- Move semantics [[video](https://www.youtube.com/watch?v=St0MNEU5b0o&ab_channel=CppCon)]


# c++ libraries
- Folly [github](https://github.com/facebook/folly)


# Optimized c++

- https://www.thegeekstuff.com/2015/01/c-cpp-code-optimization/
- Optimized C++ [[book](https://www.oreilly.com/library/view/optimized-c/9781491922057/)]
- C++ High Performance: Master the art of optimizing the functioning of your C++ code
- Effective Modern C++: 42 Specific Ways to Improve Your Use of C++11 and C++14
- Effective C++: 55 Specific Ways To Improve Your Programs And Designs
- C++ High Performance: Boost and optimize the performance of your C++17 code
- C++ Concurrency in Action
- C++ Move Semantics

# Multicore Programming

For more details, use the following resources:
- Multicore Programming [[MITOpenCourseWare](https://www.youtube.com/watch?v=dx98pqJvZVk&ab_channel=MITOpenCourseWare)]

# C++ Notes

## const map

It is important to note the difference between `map_name[key]` and `map_name.at(key)`, specifically when using a constant map.
- `mapped_type& operator[] (const key_type& k)`
  - If k matches the key of an element in the container, the function returns a reference to its mapped value.
  - If k does not match the key of any element in the container, the function inserts a new element with that key and returns a reference to its mapped value. Notice that this always increases the container size by one, even if no mapped value is assigned to the element (the element is constructed using its default constructor).
-  `mapped_type& at (const key_type& k)`
   - Returns a reference to the mapped value of the element identified with key k. If k does not match the key of any element in the container, the function throws an out_of_range exception.

So use `at()` when you want to access a constant map. I prefer to use at() for reading purpose comapred to `[]`.

## Virtual function and inheritance

Check these resources:
- [Memory Layout of C++ Object in Different Scenarios](http://www.vishalchovatiya.com/memory-layout-of-cpp-object/#:~:text=In%20the%20inheritance%20model%2C%20a,the%20class%20by%20the%20compiler.)
- [Memory Model of Objects in C++](http://jasonleaster.github.io/2015/06/13/memory-model-of-objects-in-c-plus-plus/)

## C++ Momory MOdel

A memory location is an object of scalar type (arithmetic type, pointer type, enumeration type, or std::nullptr_t)
or the largest contiguous sequence of bit fields of non-zero length

```
struct S {
    char a;     // memory location #1
    int b : 5;  // memory location #2
    int c : 11, // memory location #2 (continued)
          : 0,
        d : 8;  // memory location #3
    struct {
        int ee : 8; // memory location #4
    } e;
} obj; // The object 'obj' consists of 4 separate memory locations
```

>Note: Various features of the language, such as references and virtual functions, might involve additional memory locations that are not accessible to programs but are managed by the implementation.

> std::memory_order. What is the purpose of it?


### How does a C++ reference look, memory-wise?

> The C++ standard only says how it should behave, not how it should be implemented.

> In ISO C++, "reference is not an object". As such, it needs not have any memory representation. It's just an alias.

>  Quote from cpp primer chapter 2.3.1: A reference is not an object. Instead, a reference is just another name for an already existing object.

> C++ Standard 8.3.2/4: There shall be no references to references, no arrays of references, and no pointers to references.

Now consider few example, to understand this topic in details.

For example [[source](https://stackoverflow.com/questions/1179937/how-does-a-c-reference-look-memory-wise)],

```
void function(int& x)
{
    x = 10;
}

int main()
{
    int i = 5;
    int& j = i;

    function(j);
}
```
In the above code, j should not take space on the main stack, but the reference x of function will take a place on its stack. That means when calling function with j as an argument, the address of i that will be pushed on the stack of function. The compiler can and should not reserve space on the main stack for j.

Take another example [[source](https://stackoverflow.com/questions/1179937/how-does-a-c-reference-look-memory-wise)]:
```
#include <iostream>

using namespace std;

int main()
{
    int i = 10;
    int *ptrToI = &i;
    int &refToI = i;

    cout << "i = " << i << "\n";
    cout << "&i = " << &i << "\n";

    cout << "ptrToI = " << ptrToI << "\n";
    cout << "*ptrToI = " << *ptrToI << "\n";
    cout << "&ptrToI = " << &ptrToI << "\n";

    cout << "refToI = " << refToI << "\n";
    //cout << "*refToI = " << *refToI << "\n";
    cout << "&refToI = " << &refToI << "\n";

    return 0;
}
```
Output of this code is like this
```
i = 10
&i = 0xbf9e52f8
ptrToI = 0xbf9e52f8
*ptrToI = 10
&ptrToI = 0xbf9e52f4
refToI = 10
&refToI = 0xbf9e52f8
```
There is a deatiled explanation with assembly, check [[here](https://stackoverflow.com/questions/1179937/how-does-a-c-reference-look-memory-wise)].


Additional resources:
- [Memory Layout of C++ Object in Different Scenarios](http://www.vishalchovatiya.com/memory-layout-of-cpp-object/#:~:text=In%20the%20inheritance%20model%2C%20a,the%20class%20by%20the%20compiler.)
- [Memory Model of Objects in C++](http://jasonleaster.github.io/2015/06/13/memory-model-of-objects-in-c-plus-plus/)
- [C++11 Memory Model](https://people.cs.pitt.edu/~xianeizhang/notes/cpp11_mem.html)
- https://www.modernescpp.com/index.php/c-memory-model

## Data-Oriented vs Object-Oriented Designs

- [Data-Oriented Design (Or Why You Might Be Shooting Yourself in The Foot With OOP)](https://gamesfromwithin.com/data-oriented-design)
- [Programming Paradigms: Object Oriented vs Data Oriented](https://prateekvjoshi.com/2013/11/30/programming-paradigms-object-oriented-vs-data-oriented/)
