CURSES=@curses@
JAVAHOME=@javahome@
JAVAC=$(JAVAHOME)/bin/javac
JAR=$(JAVAHOME)/bin/jar
JAVAH=$(JAVAHOME)/bin/javah
JAVA=$(JAVAHOME)/bin/java
JAVADOC=$(JAVAHOME)/bin/javadoc

INCLUDES = -I$(JAVAHOME)/include -I$(JAVAHOME)/include/@javaos@

lib_LTLIBRARIES = src/libjcurses.la

DBGFLAGS = -g

src_libjcurses_la_CFLAGS =-Wall $(DBGFLAGS)

if HAVE_LD_VERSION_SCRIPT
    libJCurses_version_script = -Wl,--version-script=$(srcdir)/libjcurses.map
else
    libJCurses_version_script =
endif

src_libjcurses_la_SOURCES = src/native/Toolkit.c
src_libjcurses_la_LDFLAGS = -shared -fPIC -version-info $(libJCurses_api_version) -export-dynamic $(libJCurses_version_script)
src_libjcurses_la_LIBADD = -L$(libdir) -lcurses $(GLIB_LIBS)
src_libjcurses_la_DEPENDENCIES = $(srcdir)/libjcurses.map

# headers are distributed as part of the include dir
EXTRA_DIST = $(srcdir)/llnl-curses-jni-libs.spec.in \
				 $(srcdir)/libjcurses.map \
				 $(srcdir)/src/native/include/*.h \
				 $(srcdir)/config \
				 $(srcdir)/ChangeLog \
				 $(srcdir)/INSTALL \
				 $(srcdir)/README.md \
				 $(srcdir)/README_ORIG \
				 $(srcdir)/LICENSE \
			    $(srcdir)/META \
			    $(srcdir)/DISCLAIMER

dist-hook: llnl-curses-jni-libs.spec
	cp llnl-curses-jni-libs.spec $(distdir)


