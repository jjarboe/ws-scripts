ws-scripts
==========

Web services scripts

Important Files:

email\_defects.py: The main entry point.

WebService.py: a Python module that supports access to the Coverity web
               services interface.  Not normally run directly.

templates.py: Some output templates used by email\_defects.py.

cim\_charts.py: A support module for templates.py, which provides detailed
                implementations of various graphical templates.

Prerequisites
-------------

The email\_defects script relies on the "suds" module, so you must install
that before you can run email\_defects.  The "suds" module provides basic
web services support to Python.

To install "suds", you'll normally run a command like

        easy_install suds

Note that you might need root permission to install the module into a system
directory.  You might also need to install easy\_install, which is a part
of Python setuptools.

Running email\_defects.py
-------------------------

Normally, you will run the script like this:

        python email_defects.py --host <host> --port <port> --user <user> --admin <admin> [[scope]] [--test] --dest=<dest> --format=<format>

Where [[scope]] selects the defects to include in the report (e.g. --project=<project>, --status=<status>, etc.)

Running

        python email_defects.py --help

will provide detailed information about the supported options, including the
supported --dest and --format settings.

Note that the script excludes unassigned defects by default.  If you want to
include unassigned defects (including new defects), be sure to use an option
like --unassigned=include.

Adding new formats
------------------

It is possible to add your own output format to the script.  New formats will
normally be added to the file templates.py, using a symbol name like
"render_as_<format>".  The source for the existing formats is present in
that file, and can be used as a starting point for adding your own formats.
Existing formats use plain text, html, xml, and csv formats, but there
shouldn't be anything preventing you from implementing others.
