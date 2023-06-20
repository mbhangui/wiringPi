#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([wiringPi],[m4_normalize(m4_include(conf-version))],[m4_normalize(m4_include(conf-email))],[wiringpi],[https://github.com/mbhangui/wiringPi])
AM_INIT_AUTOMAKE([foreign subdir-objects silent-rules no-dist])
AC_CONFIG_SRCDIR([version.h.in])
AC_CONFIG_HEADERS([config.h])

# Checks for programs.
LT_INIT
AC_PROG_CXX
AC_PROG_CC
AC_PROG_INSTALL
AC_PROG_LN_S
AC_CONFIG_MACRO_DIR([m4])
PKG_PROG_PKG_CONFIG
PKG_INSTALLDIR

# Checks for header files.
dnl AC_CHECK_HEADERS([arpa/inet.h fcntl.h malloc.h netdb.h netinet/in.h stdint.h sys/ioctl.h sys/socket.h sys/time.h syslog.h termios.h unistd.h])

if test x$prefix = xNONE
then
	prefix="$defaultprefix"
	ac_configure_args="$ac_configure_args -prefix=$prefix"
fi
version=$VERSION
version_major=$(echo $VERSION|cut -d. -f1)
version_minor=$(echo $VERSION|cut -d. -f2)

AC_SUBST(prefix)
AC_SUBST(libdir)
AC_SUBST(pkgconfigdir)
AC_SUBST(version)
AC_SUBST(version_major)
AC_SUBST(version_minor)
DEVLIBVER=3
AC_SUBST(DEVLIBVER)
WIRINGPILIBVER=3
AC_SUBST(WIRINGPILIBVER)

AC_CONFIG_FILES([libwiringPi.pc:libwiringPi.pc.in],[], [])
AC_CONFIG_FILES([libwiringPiDev.pc:libwiringPiDev.pc.in],[], [])
AC_CONFIG_FILES([wiringPi/Makefile devLib/Makefile gpio/Makefile Makefile version.h])
AC_OUTPUT
