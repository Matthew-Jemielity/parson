VPATH = $(top_srcdir) $(top_builddir)
# Those gcc flags will be applied always upon compilation. They increase
# verbosity of warnings reported by the compiler.
AM_CFLAGS = -Wall -Wextra -pedantic
AM_CXXFLAGS = -Wall -Wextra

# Version revision tracks ALL changes to major OR minor. It's bumped whenever
# either of those values is bumped. Revision is necessary for libtool *.so
# versioning magic.
# All public version changes shall be recorded here.
PARSON_PUBLIC_VERSION_REVISION=1
PARSON_PUBLIC_VERSION_MAJOR=1
PARSON_PUBLIC_VERSION_MINOR=0
PARSON_PUBLIC_VERSION_PATCH=1

BASE_INCLUDES = -I$(top_srcdir)
BASE_FLAGS =
BASE_FLAGS += -DPARSON_PUBLIC_VERSION="\"$(PARSON_PUBLIC_VERSION_MAJOR).$(PARSON_PUBLIC_VERSION_MINOR).$(ISW_ALTERNATIVE_MASTER_PROJECT_VERSION_PATCH)\""
BASE_FLAGS += -DPARSON_RESOURCE_DIR="\"$(abs_top_srcdir)/\""

EXTRA_DIST = package.json tests

lib_LTLIBRARIES = libparson.la
libparson_la_SOURCES = \
  parson.h \
  parson.c
libparson_la_CPPFLAGS = ${BASE_INCLUDES} ${BASE_FLAGS}
libparson_la_LDFLAGS = -version-info $(PARSON_PUBLIC_VERSION_REVISION):$(PARSON_PUBLIC_VERSION_PATCH):$(PARSON_PUBLIC_VERSION_MINOR)

api_base_dir = $(includedir)/parson
api_base__HEADERS = parson.h

tests.cpp: tests.c
	ln -s $(abs_top_srcdir)/tests.c $@

CLEANFILES = tests.cpp

PARSON_UNIT_TESTS = \
  testlib \
  testc \
  testcpp

TESTS = $(PARSON_UNIT_TESTS)
check_PROGRAMS = $(PARSON_UNIT_TESTS)

TEST_C_FLAGS = -O0 -g ${BASE_FLAGS}
TEST_CXX_FLAGS = -O0 -g ${BASE_FLAGS}
TEST_CPP_FLAGS = ${BASE_INCLUDES}
TEST_LD_FLAGS =
TEST_LDADD = libparson.la

testlib_SOURCES = tests.c
testlib_CFLAGS = ${TEST_C_FLAGS}
testlib_CPPFLAGS = ${TEST_CPP_FLAGS}
testlib_LDFLAGS = ${TEST_LD_FLAGS}
testlib_LDADD = ${TEST_LDADD}

testc_SOURCES = tests.c parson.c
testc_CFLAGS = ${TEST_C_FLAGS}
testc_CPPFLAGS = ${TEST_CPP_FLAGS}
testc_LDFLAGS = ${TEST_LD_FLAGS}

testcpp_SOURCES = tests.cpp parson.c
testcpp_CXXFLAGS = ${TEST_CXX_FLAGS}
testcpp_CPPFLAGS = ${TEST_CPP_FLAGS}
testcpp_LDFLAGS = ${TEST_LD_FLAGS}

# Adds check-valgrind make target, which will check all binaries against the
# valgrind suite of tools.
@VALGRIND_CHECK_RULES@

