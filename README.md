# Homework Assignment 11

[![Build Status](https://travis-ci.com/PGE383-HPC/assignment11.svg?token=SnMGq692xXXqxzyE6QSj&branch=master)](https://travis-ci.com/PGE383-HPC/assignment11)

In [Assignment 10](https://github.com/PGE383-HPC-Spring2018/assignment10) we used [SWIG](www.swig.org) to generate Python "wrappers" to some C code to be called from a Python script that solves the Laplace equation in two dimensions.  If you recall, there were several manual steps which included calls to SWIG and a complicated compiler command to generate the compiled library.  Your task in this assignment is to use CMake to automate these steps.  Look at the file `CMakeLists.txt` in the `src` directory.  There are some comments that indicate where you should add CMake commands.

**Tips**:

 1. You will need to build a static library from the source file `iterate.c`.  This file has to be compiled with a C compiler that uses the C99 standard.  Look at the [`set_property()`](https://cmake.org/cmake/help/v3.9/command/set_property.html) CMake command for a way to enforce C99 compilation.

 2. You will need to generate a SWIG Python interface from the `iterate.i` file.  Look at the [`swig_add_module()`](https://cmake.org/cmake/help/v3.9/module/UseSWIG.html) command.  You will then need to link the SWIG module to the library you created from `iterate.c`


## Testing

If you would like to check to see if your solution is correct, run the following commands in sequence at the Terminal command line:

```bash
>mkdir build
>cd build
>cmake ..
>make
>ctest
```
