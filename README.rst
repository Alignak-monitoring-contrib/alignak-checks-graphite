Alignak checks package for Carbon/Graphite
==========================================

*Checks pack for monitoring Graphite with the monitoring package (only TCP checks)*


.. image:: https://badge.fury.io/py/alignak_checks_graphite.svg
    :target: https://badge.fury.io/py/alignak-checks-graphite
    :alt: Most recent PyPi version

.. image:: https://img.shields.io/badge/IRC-%23alignak-1e72ff.svg?style=flat
    :target: http://webchat.freenode.net/?channels=%23alignak
    :alt: Join the chat #alignak on freenode.net

.. image:: https://img.shields.io/badge/License-AGPL%20v3-blue.svg
    :target: http://www.gnu.org/licenses/agpl-3.0
    :alt: License AGPL v3


**Note:** *this check pack is only an example for checking graphite using the Nagios check_tcp command. Please feel free to comment or suggest improvements :)*

This package uses the `check_graphite_status` script from `this project <https://github.com/regilero/check_graphite_status>`_. A version of the script is included to make installation easier but you may refresh when installing...


Installation
------------

The installation of this checks pack will copy some configuration files in the Alignak default configuration directory (eg. */usr/local/etc/alignak*). The copied files are located in the default sub-directory used for the packs (eg. *arbiter/packs*).

Depending upon your OS installation you may need to install some PERL dependencies:
::

    sudo cpan install LWP

From PyPI
~~~~~~~~~
To install the package from PyPI:
::

   sudo pip install alignak-checks-graphite


From source files
~~~~~~~~~~~~~~~~~
To install the package from the source files:
::

   git clone https://github.com/Alignak-monitoring-contrib/alignak-checks-graphite
   cd alignak-checks-graphite
   sudo pip install .

**Note:** *using `sudo python setup.py install` will not correctly manage the package configuration files! The recommended way is really to use `pip`;)*

Documentation
-------------

Configuration
~~~~~~~~~~~~~

This checks pack is using the `check_tcp` Nagios (or Monitoring) plugin that must be installed on the Alignak server running your poller daemon. You may install the `alignak-checks-monitoring` package (see the `corresponding repo <https://github.com/alignak-monitoring-contrib/alignak-checks-monitoring>`_).


Alignak configuration
~~~~~~~~~~~~~~~~~~~~~

For a Linux monitored host, you simply have to tag the concerned host with the template ``graphite``.
::

    # An host with an graphite instance running
    define host{
        use                     graphite
        host_name               my_es
        address                 127.0.0.1
    }



When using the alignak backend, use the `setup.sh` script provided in the *json/graphite* directory to include all the package information into your backend
::

    # Backend configuration
    $ json/graphite/setup.sh -b http://127.0.0.1:5000 -u admin -p admin


**Note** that this command line is executed when installing the package from *pip*. If your backend is not set locally, you can specify its address thanks to the `-b` command line parameter.


Bugs, issues and contributing
-----------------------------

Contributions to this project are welcome and encouraged ... `issues in the project repository <https://github.com/alignak-monitoring-contrib/alignak-checks-graphite/issues>`_ are the common way to raise an information.
