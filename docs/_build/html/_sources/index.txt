.. Logger documentation master file, created by
   sphinx-quickstart on Fri Jan 25 12:44:10 2013.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to Logger's documentation!
==================================

A super simple logger based on Python's logger.

Installation
------------

Download the logger.php file.

Include the file where you want to log.

.. code-block:: php

    require_once 'path_to_logger/logger.php';


Logging
-------

Logger provides the API functions ``logger``, ``debug``, ``info``, ``warning`` 
``error`` and ``critical`` for logging message.


All logs called with ``logger`` are declared global so it is possible to use 
the same logger reference in different contexts with coupling the log object.

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