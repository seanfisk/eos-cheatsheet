=================================
 Machine/OS/Software Information
=================================

Finding OS versions
===================

The command:: 

	lsb_release -a

will provide the linux standard base (LSB) version, Distributor ID, OS Description, Release version, and codename.

*Sample Output*::

	No LSB modules are available.
	Distributor ID: CentOS
	Description:    CentOS release 6.5 (Final)
	Release:        6.5
	Codename:       Final


Finding versions of programs
============================

The typical command to determine the program in your path would be the following::

	<program name> --version

This is a defacto standard, thus may not work for all programs.  Be concious that there is no standard for displaying the version of the program, thus other unnessary information may be provided. 

*Sample*::

	$ python --version
	Python 2.7.5


Hardware Information
====================

Additional useful commands can be found at `binary tides <http://www.binarytides.com/linux-commands-hardware-info/>`_.
