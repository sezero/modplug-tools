AC_PREREQ(2.53)
AC_INIT
AC_CONFIG_AUX_DIR([build-aux])
AM_INIT_AUTOMAKE([modplugtools],[0.5.3])
AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_SRCDIR([mp123/modplug123.c])
AM_MAINTAINER_MODE

AC_CANONICAL_HOST

dnl save $CFLAGS since AC_PROG_CC likes to insert "-g -O2" if $CFLAGS is blank
dnl cflags_save="$CFLAGS"
AC_PROG_CC
dnl CFLAGS="$cflags_save"
if test $ac_cv_c_compiler_gnu = yes; then
   CFLAGS="$CFLAGS -Wall"
fi

dnl --------------------------------------------------
dnl System checks
dnl --------------------------------------------------

AC_USE_SYSTEM_EXTENSIONS
AC_SYS_LARGEFILE
AC_C_BIGENDIAN

PKG_CHECK_MODULES(LIBMODPLUG, libmodplug >= 0.8.8, have_modplug=yes, have_modplug=no)
if test "x$have_modplug" = "xno"; then
	AC_MSG_ERROR(libmodplug >= 0.8.8 required)
fi

PKG_CHECK_MODULES(AO, ao >= 0.8.0,,[build_modplug123=no;
		AC_MSG_WARN(libao too old; >= 0.8.0 required)]
)

AC_CHECK_HEADERS([fcntl.h sys/ioctl.h sys/time.h ])

AC_CONFIG_FILES([Makefile
          mpplay/Makefile
          mp123/Makefile])
AC_CONFIG_HEADERS([config.h])
AC_OUTPUT
