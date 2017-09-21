AC_INIT(riscv-llvm-toolchain, 1.0)

#AC_PROG_CC

AC_PATH_PROG([CMAKE], [cmake],
        [AC_MSG_ERROR([cmake not found])])

AC_SUBST(CMAKE)

AC_ARG_WITH(arch,
	[AS_HELP_STRING([--with-arch=rv64ima],
		[Sets the base RISC-V ISA, defaults to rv64ima])],
        [AS_CASE([$with_arch],
                [*rv*g* | *rv*d* | *rv*f*], [AC_MSG_ERROR([Unsupport F/D yet])],
                [*rv32* | *rv64*], [],
                [AC_MSG_ERROR([Unknown arch])])],
	[with_arch=rv64ima]
	)

AC_SUBST(WITH_ARCH, $with_arch)

AC_ARG_WITH(build_type,
	[AS_HELP_STRING([--with-build-type=Release],
		[Set the build type for LLVM, defaults to Release, Possible values are Release, Debug, RelWithDebInfo and MinSizeRel.])],
        [AS_CASE([$with_build_type],
                [Release | Debug | RelWithDebInfo | MinSizeRel], [],
                [AC_MSG_ERROR([Unknown build type, Possible values are Release, Debug, RelWithDebInfo and MinSizeRel.])])],
	[with_build_type=Release]
	)

AC_SUBST(WITH_BUILD_TYPE, $with_build_type)

AC_ARG_ENABLE(clang_only,
	[AS_HELP_STRING([--enable-clang-only=no],
		[Install clang only, and do not install another llvm tool and libraries])])

AS_IF([test "x$enable_clang_only" != "xyes"],
      AC_SUBST(BUILD_CLANG_ONLY, no),
      AC_SUBST(BUILD_CLANG_ONLY, yes))

ac_configure_args="$ac_configure_args --with-arch=$with_arch"
AC_CONFIG_SUBDIRS(riscv-gnu-toolchain)

AC_CONFIG_FILES([Makefile])

AC_OUTPUT
