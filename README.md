Building an Experimental Operating System.

## eXpOS Kernel Development Overview

In this project, we will develop the eXpOS kernel for the eXperimental String Machine (XSM). Our primary goal is to implement a kernel that can load and execute application programs. Additionally, we will write a few application programs, such as a shell, to provide a user interface.

### System Interfaces

To write the OS kernel, we need to understand two key interfaces:
1. **Architecture Interface**: Provided in the XSM architecture specification, this defines how our kernel will interact with the machine's architecture.
2. **Application Binary Interface (ABI)**: This defines how our kernel will interface with executable application programs.

In addition to these, there are two more crucial interfaces:

1. **eXpFS File System Specification**: This standardizes the format in which data and executable files are stored on the disk, ensuring file portability between eXpOS and other systems. Our OS file system must comply with this specification.
2. **eXpOS Library Specification**: This small application layer software acts as an intermediary between the OS kernel and other application programs, providing a generic interface for accessing OS system calls and dynamic memory management. The library code will be supplied to us, and our OS kernel must load this library into memory and link it to the application programs at runtime.

### Development Environment

Starting from a bare machine with no software, we require external mechanisms to:
1. Write kernel modules and convert them into XSM executable programs.
2. Store these modules on the machine's disk so they can be loaded into memory and executed when the machine is powered on.

For these tasks, we are provided with:
- **SPL Compiler**: A cross compiler for the System Programming Language (SPL), an enriched XSM assembly language. We will write OS modules in SPL, compile them in our host (Linux/Unix) environment, and generate XSM target programs using this compiler.
- **XFS Interface Tool**: This software interface allows us to transfer executable kernel modules from our host system to specified blocks on the XSM disk, thereby loading them into the appropriate areas.

Similarly, for application program development:
- **ExpL Compiler**: A cross compiler for the Experimental Language (ExpL), a tiny high-level programming language. The ExpL compiler translates our program into the target executable format recognized by eXpOS.
- **XFS Interface Tool**: This tool will also be used to store ExpL-compiled programs on the XSM machine's disk.

### Execution

The OS we build will be elementary, capable only of loading and executing programs pre-loaded onto the machine's disk before boot-up. To write application programs or kernel code, we will work from our host system, compile the code using the ExpL or SPL cross compiler, and pre-load the executable onto the XSM disk using the XFS Interface tool before powering on the simulator.

Once all OS modules and application programs are loaded onto the XSM machine's disk, the XSM simulator will be used to bootstrap the OS into the machine memory and initiate execution.

The collection of development tools provided to us, including the XSM simulator, ExpL and SPL compilers, and the XFS Interface, is referred to as the "eXpOS package" in the eXpOS documentation.

### Conclusion

By the end of this project, we will have developed a basic OS capable of managing application execution, laying the foundation for further exploration and development in system programming.
