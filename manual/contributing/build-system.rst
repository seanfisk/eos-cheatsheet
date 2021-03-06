========================
 Using the Build System
========================

Configure the Build
===================

For building the documents, we use Waf_ as a build system. Waf is similar to build systems like Autotools_ and CMake_ in that it has separate configuration and build stages. To configure the project, run::

   ./waf configure --dev-mode

.. important:: Waf may warn about a missing :cmd:`makeglossaries` tool. This is safe to ignore.

Waf will check that all the requirements are met before preparing the build. If any besides :cmd:`makeglossaries` are not met, please re-check your steps in :ref:`contributing-prereqs` or `report an issue`_. The ``--dev-mode`` disables auto-update of operations that require SSH. Since the deployment of |title| is automated, there is no reason for a contributor to leave auto-update on. A shortcut for this command is::

   ./waf configure -d

.. _contributing-build-docs:

Build the Documentation
=======================

The entire project can be built with::

   ./waf build

You will see various build steps being executed as they are printed to the screen. This command builds both the manual and the poster and places the build artifacts in the :file:`build/manual` and :file:`build/poster` directories, respectively.

If you are only interested in one output, you can restrict the build by running *one* of the following::

   ./waf html
   ./waf pdf
   ./waf man
   ./waf info
   ./waf poster

.. _contributing-view-results:

View the Results
================

The build will create outputs in various formats. Run *one* of the following commands to build the specific format, then open it in the operating system's preferred viewer::

   ./waf ohtml
   ./waf opdf
   ./waf oman
   ./waf oinfo
   ./waf oposter

.. hint:: It is not necessary to run ``./waf build`` before running any of these commands --- for example, ``./waf ohtml`` will build the HTML docs, then open them in a browser. However, it will not update the poster, PDF, etc.

Although we'd like all the outputs to look good, we primarily focus on the HTML output.

Other commands
==============

In certain circumstances, it is useful to do a full rebuild. The command::

   ./waf clean

undoes the actions of ``./waf build``, meaning that the build artifacts are removed (but the build directory still exists). The command::

   ./waf distclean

undoes the actions of both ``./waf configure`` and ``./waf build``, meaning that the build directory is removed and the project must be re-configured to be rebuilt again.

If you would like to see (almost) exactly what a user visiting the |title| website sees, run::

   ./waf archive

This command creates the directory :file:`build/website`, which contains all the files that will be uploaded to the official website. You can then view the website in this directory with::

   xdg-open build/website/index.html

It is also possible to run multiple commands at once, for example::

   ./waf distclean configure -d build

This runs a full rebuild all in one command.

Another helpful task is::

    ./waf linkcheck

This checks the Sphinx manual for broken links, redirects, and missing anchors. It's not enabled by default because there will be many false positives, including localhost links (obviously valid only in a certain context) and some URLs which are actually fine. Nevertheless, it's a useful tool for detecting broken and outdated links. Use your best judgment. You can find the full output in :file:`build/manual/linkcheck/output.txt`.
