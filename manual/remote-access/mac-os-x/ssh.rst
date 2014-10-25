=====
 SSH
=====

Mac OS X comes preinstalled with OpenSSH, the most popular implementation of the SSH protocol. The client can be run from the command-line and is simply called ``ssh``.

.. include:: ../common/openssh/connect.rst

.. include:: ../common/openssh/fingerprints.rst

.. _mac-ssh-keys:

.. include:: ../common/keys/intro.rst

.. code-block:: bash

    ssh smithj@eos01.cis.gvsu.edu 'umask u=rwx,go= && mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys' < ~/.ssh/id_rsa.pub

.. include:: ../common/keys/outro.rst

.. include:: ../common/openssh/forwarding.rst
