
.. _zend.console.getopt.configuration:

Configuring Zend_Console_Getopt
===============================


.. _zend.console.getopt.configuration.addrules:

Adding Option Rules
-------------------

You can add more option rules in addition to those you specified in the ``Zend_Console_Getopt`` constructor, using the ``addRules()`` method. The argument to ``addRules()`` is the same as the first argument to the class constructor. It is either a string in the format of the short syntax options specification, or else an associative array in the format of a long syntax options specification. See :ref:`Declaring Getopt Rules <zend.console.getopt.rules>` for details on the syntax for specifying options.


.. _zend.console.getopt.configuration.addrules.example:

.. rubric:: Using addRules()

.. code-block:: php
   :linenos:

   $opts = new Zend_Console_Getopt('abp:');
   $opts->addRules(
     array(
       'verbose|v' => 'Print verbose output'
     )
   );

The example above shows adding the ``--verbose`` option with an alias of ``-v`` to a set of options defined in the call to the constructor. Notice that you can mix short format options and long format options in the same instance of ``Zend_Console_Getopt``.


.. _zend.console.getopt.configuration.addhelp:

Adding Help Messages
--------------------

In addition to specifying the help strings when declaring option rules in the long format, you can associate help strings with option rules using the ``setHelp()`` method. The argument to the ``setHelp()`` method is an associative array, in which the key is a flag, and the value is a corresponding help string.


.. _zend.console.getopt.configuration.addhelp.example:

.. rubric:: Using setHelp()

.. code-block:: php
   :linenos:

   $opts = new Zend_Console_Getopt('abp:');
   $opts->setHelp(
       array(
           'a' => 'apple option, with no parameter',
           'b' => 'banana option, with required integer parameter',
           'p' => 'pear option, with optional string parameter'
       )
   );

If you declared options with aliases, you can use any of the aliases as the key of the associative array.

The ``setHelp()`` method is the only way to define help strings if you declared the options using the short syntax.


.. _zend.console.getopt.configuration.addaliases:

Adding Option Aliases
---------------------

You can declare aliases for options using the ``setAliases()`` method. The argument is an associative array, whose key is a flag string declared previously, and whose value is a new alias for that flag. These aliases are merged with any existing aliases. In other words, aliases you declared earlier are still in effect.

An alias may be declared only once. If you try to redefine an alias, a ``Zend_Console_Getopt_Exception`` is thrown.


.. _zend.console.getopt.configuration.addaliases.example:

.. rubric:: Using setAliases()

.. code-block:: php
   :linenos:

   $opts = new Zend_Console_Getopt('abp:');
   $opts->setAliases(
       array(
           'a' => 'apple',
           'a' => 'apfel',
           'p' => 'pear'
       )
   );

In the example above, after declaring these aliases, ``-a``, ``--apple`` and ``--apfel`` are aliases for each other. Also ``-p`` and ``--pear`` are aliases for each other.

The ``setAliases()`` method is the only way to define aliases if you declared the options using the short syntax.


.. _zend.console.getopt.configuration.addargs:

Adding Argument Lists
---------------------

By default, ``Zend_Console_Getopt`` uses ``$_SERVER['argv']`` for the array of command-line arguments to parse. You can alternatively specify the array of arguments as the second constructor argument. Finally, you can append more arguments to those already used using the ``addArguments()`` method, or you can replace the current array of arguments using the ``setArguments()`` method. In both cases, the parameter to these methods is a simple array of strings. The former method appends the array to the current arguments, and the latter method substitutes the array for the current arguments.


.. _zend.console.getopt.configuration.addargs.example:

.. rubric:: Using addArguments() and setArguments()

.. code-block:: php
   :linenos:

   // By default, the constructor uses $_SERVER['argv']
   $opts = new Zend_Console_Getopt('abp:');

   // Append an array to the existing arguments
   $opts->addArguments(array('-a', '-p', 'p_parameter', 'non_option_arg'));

   // Substitute a new array for the existing arguments
   $opts->setArguments(array('-a', '-p', 'p_parameter', 'non_option_arg'));


.. _zend.console.getopt.configuration.config:

Adding Configuration
--------------------

The third parameter to the ``Zend_Console_Getopt`` constructor is an array of configuration options that affect the behavior of the object instance returned. You can also specify configuration options using the ``setOptions()`` method, or you can set an individual option using the ``setOption()`` method.

.. note::
   **Clarifying the Term "option"**

   The term "option" is used for configuration of the ``Zend_Console_Getopt`` class to match terminology used elsewhere in Zend Framework. These are not the same things as the command-line options that are parsed by the ``Zend_Console_Getopt`` class.


The currently supported options have const definitions in the class. The options, their const identifiers (with literal values in parentheses) are listed below:

- ``Zend_Console_Getopt::CONFIG_DASHDASH`` ("dashDash"), if ``TRUE``, enables the special flag ``--`` to signify the end of flags. Command-line arguments following the double-dash signifier are not interpreted as options, even if the arguments start with a dash. This configuration option is ``TRUE`` by default.

- ``Zend_Console_Getopt::CONFIG_IGNORECASE`` ("ignoreCase"), if ``TRUE``, makes flags aliases of each other if they differ only in their case. That is, ``-a`` and ``-A`` will be considered to be synonymous flags. This configuration option is ``FALSE`` by default.

- ``Zend_Console_Getopt::CONFIG_RULEMODE`` ("ruleMode") may have values ``Zend_Console_Getopt::MODE_ZEND`` ("zend") and ``Zend_Console_Getopt::MODE_GNU`` ("gnu"). It should not be necessary to use this option unless you extend the class with additional syntax forms. The two modes supported in the base ``Zend_Console_Getopt`` class are unambiguous. If the specifier is a string, the class assumes ``MODE_GNU``, otherwise it assumes ``MODE_ZEND``. But if you extend the class and add more syntax forms, you may need to specify the mode using this option.

More configuration options may be added as future enhancements of this class.

The two arguments to the ``setOption()`` method are a configuration option name and an option value.


.. _zend.console.getopt.configuration.config.example.setoption:

.. rubric:: Using setOption()

.. code-block:: php
   :linenos:

   $opts = new Zend_Console_Getopt('abp:');
   $opts->setOption('ignoreCase', true);

The argument to the ``setOptions()`` method is an associative array. The keys of this array are the configuration option names, and the values are configuration values. This is also the array format used in the class constructor. The configuration values you specify are merged with the current configuration; you don't have to list all options.


.. _zend.console.getopt.configuration.config.example.setoptions:

.. rubric:: Using setOptions()

.. code-block:: php
   :linenos:

   $opts = new Zend_Console_Getopt('abp:');
   $opts->setOptions(
       array(
           'ignoreCase' => true,
           'dashDash'   => false
       )
   );


