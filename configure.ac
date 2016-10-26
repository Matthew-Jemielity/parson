#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.64])
AC_INIT([parson], m4_esyscmd([git log -n 1 --format="%H" -- . | tr -d '\n']))
AC_CONFIG_AUX_DIR([.])
AC_CONFIG_SRCDIR([parson.c])
AC_CONFIG_FILES([Makefile])
AC_CONFIG_MACRO_DIR([m4])
AM_INIT_AUTOMAKE([-Wall subdir-objects tar-pax foreign])

AM_PROG_AR
AC_PROG_CC_C89
AM_PROG_CC_C_O
AC_PROG_CXX
AC_PROG_CXX_C_O
# Check for valgrind for more involved testing, macro defined in m4 directory.
AX_VALGRIND_CHECK

LT_INIT

# PACKAGE_VERSION will be set to last commit hash, sort of internal versioning.
AC_CHECK_HEADERS([ctype.h math.h stddef.h stdio.h stdlib.h string.h], [], [AC_MSG_ERROR([cannot find or include prerequisite header])])

# This command should always be last.
AC_OUTPUT

