Logger
******

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


.. logger.php generated using docpx on 01/25/13 05:40pm


LOGGER_LOG_LEVEL
++++++++++++++++

LOGGER_LOG_LEVEL

The default log level code to use when logging messages.

logger
======

.. function:: logger()


    Returns a logger identified by the given name.
    
    If the logger does not exist it is created.

    :param string: Name of the logger

    :rtype: object Logger



Logger
******


Stupid simple logging utility for PHP based on Pythons logger.



Methods
=======

instance
--------

.. function:: instance()


    Returns an instance of the singleton.
    
    Passes args to constructor



__clone
-------

.. function:: __clone()


    Disallow cloning



add_handler
-----------

.. function:: add_handler()


    Adds a handler.

    :param object: HJandler

    :rtype: void 



log
---

.. function:: log()


    Logs a message.

    :param integer: Log level code.
    :param string: Message to log.

    :rtype: void 



debug
-----

.. function:: debug()


    Logs a debug message.

    :param string: Message to log.

    :rtype: void 



info
----

.. function:: info()


    Logs a info message.

    :param string: Message to log.

    :rtype: void 



warning
-------

.. function:: warning()


    Logs a warning message.

    :param string: Message to log.

    :rtype: void 



error
-----

.. function:: error()


    Logs a error message.

    :param string: Message to log.

    :rtype: void 



critical
--------

.. function:: critical()


    Logs a critical message.

    :param string: Message to log.

    :rtype: void 



get_logger
----------

.. function:: get_logger()


    Returns a new logger.

    :param string: Name of the logger.

    :rtype: object Logger





Constants
---------

DEBUG
+++++

DEBUG

Detailed information, typically of interest only when diagnosing 
problems.

INFO
++++

INFO

Confirmation that things are working as expected.

WARNING
+++++++

WARNING 

An indication that something unexpected happened, or indicative of
some problem in the near future (e.g. ‘disk space low’). 
 
The software is still working as expected.

ERROR
+++++

ERROR

Due to a more serious problem, the software has not been able to 
perform some function.

CRITICAL
++++++++

CRITICAL   

A serious error, indicating that the program itself may be unable 
to continue running.

Handler
*******


Handler

Handles a log message



Methods
=======

__construct
-----------

.. function:: __construct()


    Sets the formatter.

    :param object: 
    :param resource: Output resource or file
    :param integer: Code level to log, anything greater than the 
                         given code will be logged.

    :rtype: void 



handle
------

.. function:: handle()


    Handles a message.

    :param integer: Log level code.
    :param string: Message to handle.

    :rtype: void 



_make_writeable
---------------

.. function:: _make_writeable()


    Makes the output writeable.
    
    This will create a non-blocking stream to the given file.

    :rtype: boolean 



Formatter
*********


Formatter

Formats a log message.

The formatter allows for the following parameters.

%date - Date of the log
%message - Log message
%code - Error Code Level
%str_code - String representation of the error code



Methods
=======

__construct
-----------

.. function:: __construct()


    Create a formatter.

    :param object: String format to log a message

    :rtype: void 



format
------

.. function:: format()


    Handles a message.

    :param integer: Log level code.
    :param string: Message to handle.

    :rtype: void 



psprintf
--------

.. function:: psprintf()


    Returns a formatted string. Accepts named arguments.



