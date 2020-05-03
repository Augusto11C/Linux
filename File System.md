1. /opt : Add-on application software packages

**Purpose**
/opt is reserved for the installation of add-on application software packages. Moreover, precompiled software that is not distributed via Debian packages goes here.

> A **software add-on** or extension is any third-party software program or script that is added to a program to give it additional features and abilities.For example, Adobe Flash, which allowed users to watch videos or play games within an Internet browser

2. /usr

    2.2. /usr/local 
     
    /usr/local is a place to install files built by the administrator, typically by using the make command (e.g., ./configure; make; make install). The idea is to avoid clashes with files that are part of the operating system, which would either be overwritten or overwrite the local ones otherwise (e.g., /usr/bin/foo is part of the OS while /usr/local/bin/foo is a local alternative)
