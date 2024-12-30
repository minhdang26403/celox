# Bytecode Virtual Machine

This project implements a bytecode virtual machine that interprets bytecode generated from a custom language. The VM operates using a register-based model and supports features such as garbage collection, classes, methods, closures, and more. The project is an essential part of building a working interpreter and is divided into several stages, from bytecode generation to runtime execution.

## Building the Project
To build the project, ensure you have `CMake` installed, along with a C compiler. Follow these steps:

1. Clone the repository and go to the project directory.

2. Create a build directory:
    ```bash
    mkdir build
    cd build
    ```

3. Run CMake:
    ```bash
    cmake ..
    ```

4. Build the project (celox VM and unit tests):
    ```bash
    cmake --build .
    ```

5. Build the celox VM only:
    ```bash
    make celox
    ```

## Running the Project

## Running Tests

## Status

The following features are currently implemented in the language:
- [ ] Chunks of Bytecode
- [ ] A Virtual Machine
- [ ] Scanning on Demand
- [ ] Compiling Expressions
- [ ] Types of Values
- [ ] Strings
- [ ] Hash Tables
- [ ] Global Variables
- [ ] Local Variables
- [ ] Jumping Back and Forth
- [ ] Calls and Functions
- [ ] Closures
- [ ] Garbage Collection
- [ ] Classes and Instances
- [ ] Methods and Initializers
- [ ] Superclasses
- [ ] Optimization