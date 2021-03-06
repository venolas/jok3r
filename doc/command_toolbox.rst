=================
Command `toolbox`
=================

The command `toolbox` allows to manage the hacking tools used by *Jok3r*.

.. code-block:: console

    usage: python3 jok3r.py toolbox <args>

    optional arguments:
      -h, --help                    show this help message and exit

    Toolbox management:
      Tools are classified by services they can target into the toolbox. Tools that may be used against various
      different services are grouped under the name "multi".

      --show <service>              Show toolbox content for a given service
      --show-all                    Show full toolbox content
      --install <service>           Install the tools for a given service
      --install-all                 Install all the tools in the toolbox
      --update <service>            Update the installed tools for a given service
      --update-all                  Update all installed tools in the toolbox
      --uninstall <service>         Uninstall the tools for a given service
      --uninstall-tool <tool-name>  Uninstall a given tool
      --uninstall-all               Uninstall all tools in the toolbox
      --fast                        Fast mode, disable prompts and post-install checks


Show the Toolbox content
========================
* ``--show <service>``: Display the list of tools that target the specified service. 
  Use ``multi`` as parameter to display the tools that target multiple services (e.g.
  *Nmap*, *Metasploit*...)

* ``--show-all``: Display all the tools in the toolbox.

.. note::
    The toolbox is defined in the configuration file ``settings/toolbox.conf``.
    It can be easily customized in order to add new tools.


Install the Tools
=================
* ``--install <service>``: Install the tools that target a given service. 

* ``--install-all``: Install all the tools in the toolbox.

.. note::
    For installing a tool, *Jok3r* runs the command(s) that is(are) defined as value
    for the key ``install`` into the ``[toolname]`` section, in the 
    ``settings/toolbox.conf`` file.


Update the Tools
================
* ``--update <service>``: Update the tools that target a given service. 

* ``--update-all``: Update all the tools in the toolbox.

.. note::
    For updating a tool, *Jok3r* runs the command(s) that is(are) defined as value
    for the key ``update`` into the ``[toolname]`` section, in the 
    ``settings/toolbox.conf`` file.


Uninstall the Tools
===================
* ``--uninstall <service>``: Uninstall the tools that target a given service. 

* ``--uninstall-tool <tool-name>``: Uninstall a given tool.

* ``--uninstall-all``: Uninstall all the tools in the toolbox.


Misc
====
By default, when installing/updating/uninstalling tools in the toolbox, *Jok3r* will
ask for confirmation for each tool. And after installing or updating a tool, it will
also ask the user to check if it has been correctly installed. To do so, *Jok3r* runs
the command defined in ``check_command`` into the ``[toolname]`` in the 
``settings/toolbox.conf`` file, and then it asks the user whether everything seems ok
(i.e. no error is displayed) or not.

This has been designed this way essentially for debugging purpose, and **human 
interaction can be avoided** by adding the option ``--fast``


Examples
========
The commands you will run most of the time are:

* **Install the whole toolbox**, just after installing *Jok3r*:

.. code-block:: console

    sudo python3 jok3r.py toolbox --install-all --fast

* **Update all the tools in the toolbox**:

.. code-block:: console

    sudo python3 jok3r.py toolbox --update-all --fast