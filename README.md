RISC-V LLVM Toolchain
=============================

This is the RISC-V LLVM C and C++ cross-compiler. It supports ELF/Newlib toolchain only in this moment.

###  Getting the sources

This repository uses submodules. You need the --recursive option to fetch the submodules automatically

    $ git clone --recursive https://github.com/andestech/riscv-llvm-toolchain.git

### Installation

To build the Newlib cross-compiler, pick an install path.  If you choose,
say, `/opt/riscv`, then add `/opt/riscv/bin` to your `PATH` now.  Then, simply
run the following command:

    ./configure --prefix=/opt/riscv
    make

You should now be able to use riscv-llvm and its cousins.

The build defaults to targetting RV64IMC (64-bit), even on a 32-bit build
environment.  To build the 32-bit RV32IMC toolchain, use:

    ./configure --prefix=/opt/riscv --with-arch=rv32imc
    make

Supported architectures are rv32i or rv64i plus standard extensions (a)tomics,
(m)ultiplication and division.

### Usage

You can found a LLVM toolchain in your install path, we recommand you use `riscv32-elf-unknown-clang` (or `riscv64-elf-unknown-clang` for RV64) to compile program just like `riscv32-elf-unknown-gcc` instead of use clang directly.

### Advanced Options

There are a number of additional options that may be passed to
configure.  See './configure --help' for more details.
