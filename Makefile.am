AUTOMAKE_OPTIONS = foreign subdir-objects
AM_CFLAGS = -Wall -Werror -std=c11
AM_CXXFLAGS = -Wall -Werror -std=c++11 -I./Common -I./Common/pbkdf2 -I./linux -I./LinuxPBA

# Shared library for Python bindings
lib_LTLIBRARIES = libsedutil.la

libsedutil_la_SOURCES = \
	Common/DtaAnnotatedDump.cpp \
	Common/DtaCommand.cpp \
	Common/DtaDev.cpp \
	Common/DtaDevEnterprise.cpp \
	Common/DtaDevGeneric.cpp \
	Common/DtaDevOpal1.cpp \
	Common/DtaDevOpal2.cpp \
	Common/DtaDevOpalite.cpp \
	Common/DtaDevPyrite1.cpp \
	Common/DtaDevPyrite2.cpp \
	Common/DtaDevRuby1.cpp \
	Common/DtaDevOpal.cpp \
	Common/DtaDiskType.cpp \
	Common/DtaHashPwd.cpp \
	Common/DtaHexDump.cpp \
	Common/DtaResponse.cpp \
	Common/DtaSession.cpp \
	Common/DtaOptions.cpp \
	Common/pbkdf2/blockwise.c \
	Common/pbkdf2/chash.c \
	Common/pbkdf2/hmac.c \
	Common/pbkdf2/pbkdf2.c \
	Common/pbkdf2/sha1.c \
	linux/DtaDevLinuxNvme.cpp \
	linux/DtaDevLinuxSata.cpp \
	linux/DtaDevOS.cpp

libsedutil_la_LDFLAGS = -version-info 1:15:0

# Install headers for Python bindings in sedutil subdirectory
sedutilincludedir = $(includedir)/sedutil
sedutilinclude_HEADERS = \
	Common/DtaAnnotatedDump.h \
	Common/DtaCommand.h \
	Common/DtaDev.h \
	Common/DtaDevEnterprise.h \
	Common/DtaDevGeneric.h \
	Common/DtaDevOpal1.h \
	Common/DtaDevOpal2.h \
	Common/DtaDevOpalite.h \
	Common/DtaDevPyrite1.h \
	Common/DtaDevPyrite2.h \
	Common/DtaDevRuby1.h \
	Common/DtaDevOpal.h \
	Common/DtaDiskType.h \
	Common/DtaHashPwd.h \
	Common/DtaHexDump.h \
	Common/DtaResponse.h \
	Common/DtaSession.h \
	Common/DtaStructures.h \
	Common/log.h \
	Common/DtaLexicon.h \
	Common/DtaConstants.h \
	Common/DtaEndianFixup.h \
	Common/DtaOptions.h \
	linux/DtaDevLinuxNvme.h \
	linux/DtaDevLinuxSata.h \
	linux/DtaDevOS.h \
	linux/DtaDevLinuxDrive.h \
	linux/os.h

# PBKDF2 headers in sedutil/pbkdf2 subdirectory
pbkdf2dir = $(includedir)/sedutil/pbkdf2
pbkdf2_HEADERS = \
	Common/pbkdf2/blockwise.h \
	Common/pbkdf2/chash.h \
	Common/pbkdf2/handy.h \
	Common/pbkdf2/hmac.h \
	Common/pbkdf2/pbkdf2.h \
	Common/pbkdf2/sha1.h \
	Common/pbkdf2/tassert.h \
	Common/pbkdf2/bitops.h

sbin_PROGRAMS = sedutil-cli linuxpba

sedutil_cli_SOURCES = linux/Version.h Common/sedutil.cpp
sedutil_cli_LDADD = libsedutil.la
CLEANFILES = linux/Version.h
BUILT_SOURCES = linux/Version.h
#
linuxpba_SOURCES = LinuxPBA/LinuxPBA.cpp LinuxPBA/GetPassPhrase.cpp LinuxPBA/UnlockSEDs.cpp \
	 LinuxPBA/GetPassPhrase.h LinuxPBA/UnlockSEDs.h
linuxpba_LDADD = libsedutil.la
EXTRA_DIST = linux/GitVersion.sh linux/PSIDRevert_LINUX.txt linux/TestSuite.sh README.md docs/sedutil-cli.8
man_MANS = docs/sedutil-cli.8
linux/Version.h:
	./linux/GitVersion.sh > linux/Version.h
.INTERMEDIATE: linux/Version.h

