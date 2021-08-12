


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
- [Memory Layout of C++ Object in Different Scenarios](http://www.vishalchovatiya.com/memory-layout-of-cpp-object/#:~:text=In%20the%20inheritance%20model%2C%20a,the%20class%20by%20the%20compiler.)
- [Memory Model of Objects in C++](http://jasonleaster.github.io/2015/06/13/memory-model-of-objects-in-c-plus-plus/)
- [C++11 Memory Model](https://people.cs.pitt.edu/~xianeizhang/notes/cpp11_mem.html)
