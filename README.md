RISC-V LLVM Toolchain
=============================

[![Build Status](https://travis-ci.org/riscv/riscv-gnu-toolchain.svg?branch=master)](https://travis-ci.org/riscv/riscv-gnu-toolchain)

This is the RISC-V C and C++ cross-compiler. It supports ELF/Newlib toolchain only in this moment.

###  Getting the sources

This repository uses submodules. You need the --recursive option to fetch the submodules automatically

    $ git clone --recursive https://github.com/riscv/riscv-llvm-toolchain

### Prerequisites

Several standard packages are needed to build the toolchain.  On Ubuntu,
executing the following command should suffice:

    $ sudo apt-get install autoconf automake autotools-dev curl libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev

On Fedora/CentOS/RHEL OS, executing the following command should suffice:

    $ sudo yum install autoconf automake libmpc-devel mpfr-devel gmp-devel gawk  bison flex texinfo patchutils gcc gcc-c++ zlib-devel

On OS X, you can use [Homebrew](http://brew.sh) to install the dependencies:

    $ brew install gawk gnu-sed gmp mpfr libmpc isl zlib

To build the glibc (Linux) on OS X, you will need to build within a case-sensitive file
system.  The simplest approach is to create and mount a new disk image with
a case sensitive format.  Make sure that the mount point does not contain spaces. This is not necessary to build newlib or gcc itself on OS X.

This process will start by downloading about 200 MiB of upstream sources, then
will patch, build, and install the toolchain.  If a local cache of the
upstream sources exists in $(DISTDIR), it will be used; the default location
is /var/cache/distfiles.  Your computer will need about 8 GiB of disk space to
complete the process.

### Installation (Newlib)

To build the Newlib cross-compiler, pick an install path.  If you choose,
say, `/opt/riscv`, then add `/opt/riscv/bin` to your `PATH` now.  Then, simply
run the following command:

    ./configure --prefix=/opt/riscv
    make

You should now be able to use riscv-gcc and its cousins.

The build defaults to targetting RV64IMC (64-bit), even on a 32-bit build
environment.  To build the 32-bit RV32IMC toolchain, use:

    ./configure --prefix=/opt/riscv --with-arch=rv32imc
    make

Supported architectures are rv32i or rv64i plus standard extensions (a)tomics,
(m)ultiplication and division.

### Advanced Options

There are a number of additional options that may be passed to
configure.  See './configure --help' for more details.
