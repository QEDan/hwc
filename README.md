# hwc
Hello World Compiler

hwc is the Hello World compiler. This compiler will take input source code written in *any programming language* and compile it into a Hello World program binary. The compiler even works with new languages that do not yet have a compiler. Furthermore, it works with interpreted languages as well. 

This tool is intended to accelerate the development of new programming languages. Language developers will no longer need to develop a specialized compiler or interpreter for their language before being able to demonstrate it and introduce it to the world. 

Another use case for hwc is for learners of a new language. For those who are new to a language, getting the syntax of input files can be difficult at times. It can also be frustrating to install and configure more complicated compilers and interpreters before they will successfully compile your hello world programs. hwc can compile your input files into a hello world program even if it contains syntax errors, typos, or total nonsense.

# Installation

The hwc source file should be given execute permissions and installed to a directory on the user's path. hwc is a simple program that depends on python >= 2.7 running in a Unix-like environment. Moreover, it uses gcc as a backend, but this can be easily changed to another c compiler by modifying the source.

# Usage and tutorial
To use hwc, you specify an output file using the -o option and a list of (any language) source files and libraries to link.
```
$ ./hwc --help
Usage: hwc [options] file1 file2 ...

Options:
  -h, --help            show this help message and exit
  -o OUTFILE, --outfile=OUTFILE
                        File name of the compiled binary
```

First, lets compile a hello world program written in C:
```
$ echo '#include<stdio.h>\nint main(){ printf(\"Hello world!\\n\"); exit 0; }' > hello.c
$ hwc -o hello_in_c hello.c
$ ./hello_in_c
Hello world!
```
We can use any language we want. Try python:
```
$ echo 'print("Hello world!")' > hello.py
$ hwc -o hello_in_py hello.py
$ ./hello_in_py
Hello world!
```

Note that the input file can be in new languages that don't have a compiler yet:
```
$ echo 'This isn't even a real programming language!!!' > source.nonsense
$ hwc -o hello_in_nonsense source.nonsense
$ ./hello_in_nonsense
Hello world!
```
Source input is actually optional. We can bootstrap hello world binaries from vacuum fluctuations:
```
$ hwc -o hello_from_scratch
$ ./hello_from_scratch
Hello world!
```
