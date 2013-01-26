.. Logger documentation master file, created by
   sphinx-quickstart on Fri Jan 25 12:44:10 2013.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to Logger's documentation!
==================================

A super simple logger based on Python's logger.

Installation
------------

Download the latest_.

_latest: https://github.com/prggmr/logger/archive/master.zip

Include in configuration.

.. code-block:: php

    require_once 'logger.php';

Logging
-------

Logger aims to provide a dead simple API based on Python's logger.

Logging is performed using the ``logger`` function.

This returns a ``Logger`` object used to log using the methods ``debug``, 
``info``, ``warning``, ``error``, ``critical``.

Log to STDOUT
-------------

Create a new logger and send output to STDOUT.

.. code-block:: php

    <?php

    $log = logger('foo-log');
    $formatter = new Formatter(
        '[{date}] [{str_code}] {message}'.PHP_EOL
    );
    $log->add_handler(new Handler(
        $formatter, STDOUT
    ));

    $log->info('About to perform foo action');

Logging to multiple files at once
---------------------------------

Creates a new logger and sends output to STDOUT and log file.

.. code-block:: php

    <?php

    $log = logger('foo-log');
    $formatter = new Formatter(
        '[{date}] [{str_code}] {message}'.PHP_EOL
    );
    $log->add_handler(new Handler(
        $formatter, STDOUT
    ));
    $log->add_handler(new Handler(
        $formatter, '/tmp/foo.log'
    ));

API
---

.. toctree::
   :maxdepth: 3
   :glob:

   logger