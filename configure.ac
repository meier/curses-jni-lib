dnl Process this file with autoconf to produce a configure script.

AC_INIT(llnl-curses-jni-libs, 1.0.0, meier3@llnl.gov)
AC_META
AC_CONFIG_AUX_DIR(config)
AC_CONFIG_SRCDIR([META])
AM_CONFIG_HEADER(config.h)
AM_INIT_AUTOMAKE($PROJECT, $VERSION)

dnl Checks for programs
AC_PROG_CC
AC_PROG_GCC_TRADITIONAL
AC_PROG_LIBTOOL

AC_PATH_PROG(javahome,java, "/usr/bin")
javahome=`dirname ${javahome}`
javahome=`dirname ${javahome}`
echo "JAVAHOME=${javahome}"
for each in `ls ${javahome}/include` ;do
  if [ test -d ${javahome}/include/${each} ] ;then
     javaos=${each}
  fi;
done;
echo "JAVAOS=${javaos}"
AC_SUBST(javaos)
AC_CHECK_PROG(gcc,gcc,gcc)
AC_PROG_CC

dnl OpenSM headers are in $includedir/infiniband
INC_TMP1="`eval echo ${includedir}`"
INC_TMP2="`echo $INC_TMP1 | sed 's/^NONE/$ac_default_prefix/'`"
CFLAGS="$CFLAGS -I`eval echo $INC_TMP2`"
CPPFLAGS="$CPPFLAGS -I`eval echo $INC_TMP2`"

dnl Checks for libraries
AC_CHECK_LIB(curses,initscr,curses=-lcurses)
AC_CHECK_LIB(ncurses,initscr,curses=-lncurses)

AC_SUBST(curses)

dnl the library version
libJCurses_api_version=1:1:0
AC_SUBST(libJCurses_api_version)

dnl We use --version-script with ld if possible
AC_CACHE_CHECK(whether ld accepts --version-script, ac_cv_version_script,
    if test -n "`$LD --help < /dev/null 2>/dev/null | grep version-script`"; then
        ac_cv_version_script=yes
    else
        ac_cv_version_script=no
    fi)

AM_CONDITIONAL(HAVE_LD_VERSION_SCRIPT, test "$ac_cv_version_script" = "yes")

# we have to revive the env CFLAGS as some how they are being overwritten...
# see http://sources.redhat.com/automake/automake.html#Flag-Variables-Ordering
# for why they should NEVER be modified by the configure to allow for user
# overrides.
CFLAGS=$ac_env_CFLAGS_value


AC_CONFIG_FILES([jcurses_version.h \
		Makefile \
		llnl-curses-jni-libs.spec \
		])
AC_OUTPUT


