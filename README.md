# curses-jni-lib
Java Native Interface between the ncurses library and the curses-java-api library

Overview
-------------------------

The **jcurses** library is the native interface wrapper between the standard ncurses package and the **jcurses.jar** java library.

The original package was found on SourceForge (http://sourceforge.net/projects/javacurses/) and contained both the native C and java
code in the same repository.  It has been separated.  It appears like the original project has
been abandoned.  It has been divided and repackaged, to build with gradle, but has almost no code changes.

Standard Build
-------------------------

This package includes all the necessary and standard build files.  From the top level directory;

./autogen.sh 
./configure
make
make dist
rpmbuild -ta *.tar.gz
