============================
Sentry Logs |latest-version|
============================

|build-status| |health| |python-support| |downloads| |license|

Sentry Logs allows you to send logs to Sentry.  Only Nginx error log is
currently supported, but extending the library to support more log files
is planned.


.. |latest-version| image:: https://img.shields.io/pypi/v/sentrylogs.svg
   :alt: Latest version on PyPI
   :target: https://pypi.python.org/pypi/sentrylogs
.. |build-status| image:: https://travis-ci.org/mdgart/sentrylogs.svg
   :alt: Build status
   :target: https://travis-ci.org/mdgart/sentrylogs
.. |health| image:: https://landscape.io/github/mdgart/sentrylogs/master/landscape.svg?style=flat
   :target: https://landscape.io/github/mdgart/sentrylogs/master
   :alt: Code health
.. |python-support| image:: https://img.shields.io/pypi/pyversions/sentrylogs.svg
   :target: https://pypi.python.org/pypi/sentrylogs
   :alt: Python versions
.. |downloads| image:: https://img.shields.io/pypi/dm/sentrylogs.svg
   :alt: Monthly downloads from PyPI
   :target: https://pypi.python.org/pypi/sentrylogs
.. |license| image:: https://img.shields.io/pypi/l/sentrylogs.svg
   :alt: Software license
   :target: https://github.com/mdgart/sentrylogs/blob/master/LICENSE.txt

How it works
============

To install *sentrylogs* you can use pip or easy_install::

    pip install sentrylogs

or::

    easy_install sentrylogs

This will install the module and will provide a new console command::

    $ sentrylogs -h

    usage: sentrylogs [-h] [--follow FOLLOW] [--sentrydsn SENTRYDSN] [--daemonize]
                      [--nginxerrorpath NGINXERRORPATH]

    Send logs to Django Sentry.

    optional arguments:
      -h, --help            show this help message and exit
      --follow FOLLOW, -f FOLLOW
                            Which logs to follow, default ALL (for now only ALL is available)
      --sentrydsn SENTRYDSN, -s SENTRYDSN
                            The Sentry DSN string
      --daemonize, -d       Run this script in background
      --nginxerrorpath NGINXERRORPATH, -n NGINXERRORPATH
                            Nginx error log path

You must provide a Sentry DSN to make it work; you have 2 possibilities:

Provide an environment variable::

    $ export SENTRY_DSN="protocol://public:secret@example.com/#"
    $ sentrylogs

or use the ``--sentrydsn`` command line argument::

    $ sentrylogs --sentrydsn "protocol://public:secret@example.com/#"

By default *sentrylogs* will assume the nginx log at ``/var/log/nginx/error.log``,
but you can change this using the ``--nginxerrorpath`` argument.

If you use ``--daemonize`` the command will daemonize itself and run in
background.