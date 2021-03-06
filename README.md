[![Build Status](https://travis-ci.org/EIPStackGroup/OpENer.svg?branch=master)](https://travis-ci.org/EIPStackGroup/OpENer)

[![Stories in Ready](https://badge.waffle.io/EIPStackGroup/OpENer.svg?label=ready&title=Ready)](http://waffle.io/EIPStackGroup/OpENer)

OpENer Version 1.2.0
====================

Welcome to OpENer!
------------------

OpENer is an EtherNet/IP&trade; stack for I/O adapter devices; supports multiple 
I/O and explicit connections; includes objects and services to make EtherNet/IP&trade;-
compliant products defined in THE ETHERNET/IP SPECIFICATION and published by 
ODVA (http://www.odva.org).

Requirements:
-------------
OpENer has been developed to be highly portable. The default version targets PCs
with a POSIX operating system and a BSD-socket network interface. To test this 
version we recommend a Linux PC or Windows with Cygwin (http://www.cygwin.com) 
installed. You will need to have the following installed:

* CMake
* gcc
* make
* binutils 
 
for normal building. These should be installed on most Linux installations and
are part of the development packages of Cygwin.

If you want to run the unit tests you will also have to download CppUTest via
https://github.com/cpputest/cpputest

For the development itself we recommend the use of Eclipse with the CDT plugin 
(http://www.eclipse.org).

For configuring the project we recommend the use of a CMake GUI (e.g.,the 
cmake-gui oackage on Linux)

Compile for POSIX:
----------------
1. Directly in the shell:
	1. Go into the bin/posix directory
	2. For a standard configuration invoke setup_posix.sh, otherwise start
 cmake (GUI or shell application) and configure your project
	3. Invoke make
	4. For invoking opener type:

		./OpENer ipaddress subnetmask gateway domainname hostaddress macaddress

		e.g. ./OpENer 192.168.0.2 255.255.255.0 192.168.0.1 test.com testdevice 00 15 C5 BF D0 87
 
2. Within Eclipse
	1. For a standard configuration invoke setup_posix.sh, otherwise start
 cmake (GUI or shell application) and configure your project
	2. Import the project
	3. Go to the bin/win32 folder in the make targets view
	4. Choose all from the make targets
	5. The resulting executable will be in the directory /bin/posix or the
directoy you have choosen via CMake

Compile for Windows XP/7/8:
---------------------------
1. Invoke setup_windows.bat or configure via CMake
2. Open Visual Studio solution in bin/win32

Directory structure:
--------------------
- bin ...  The resulting binaries and make files for different ports
- doc ...  Doxygen generated documentation (has to be generated for the SVN version) and Coding rules
- data ... EDS file for the default application
- source
	- src ... the production source code
		- cip ... the CIP layer of the stack
		- cip_objects ... additional CIP objects
		- enet_encap ... the Ethernet encapsulation layer
		- ports ... the platform specific code
		- utils ... utility functions
	- tests ... the test source code
		- enet_encap ... tests for Ethernet encapsulation layer
		- utils ... tests for utility functions

Documentation:
--------------
The documentation of the functions of OpENer is part of the source code. The source 
packages contain the generated documentation in the directory doc/api_doc. If you 
use the GIT version you will need the program Doxygen for generating the HTML 
documentation. You can generate the documentation by invoking doxygen from the 
command line in the opener main directory.

Porting OpENer:
---------------
For porting OpENer to new platforms please see the porting section in the 
Doxygen documentation.

Contributing to OpENer:
-----------------------
The easiest way is to fork the repository, then create a feature/bugfix branch.
After finishing your feature/bugfix create a pull request and explain your changes.
Also, please update and/or add doxygen comments to the provided code sections.
Please stick to the coding conventions, as defined in source/doc/coding_rules
The easiest way to conform to the indenting convertion is to set uncrustify as git filter in the OpENer repository, which can be done with the following to commands:

git config filter.uncrustify.clean=/path/to/uncrustify/uncrustify -c uncrustify.cfg --mtime --no-backup
git config filter.uncrustify.smudge=cat


