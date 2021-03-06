
.. _zend.filter.set.null:

Null
====

This filter will change the given input to be ``NULL`` if it meets specific criteria. This is often necessary when you work with databases and want to have a ``NULL`` value instead of a boolean or any other type.


.. _zend.filter.set.null.options:

Supported options for Zend_Filter_Null
--------------------------------------

The following options are supported for ``Zend_Filter_Null``:

- **type**: The variable type which should be supported.


.. _zend.filter.set.null.default:

Default behaviour for Zend_Filter_Null
--------------------------------------

Per default this filter works like *PHP*'s ``empty()`` method; in other words, if ``empty()`` returns a boolean ``TRUE``, then a ``NULL`` value will be returned.

.. code-block:: php
   :linenos:

   $filter = new Zend_Filter_Null();
   $value  = '';
   $result = $filter->filter($value);
   // returns null instead of the empty string

This means that without providing any configuration, ``Zend_Filter_Null`` will accept all input types and return ``NULL`` in the same cases as ``empty()``.

Any other value will be returned as is, without any changes.


.. _zend.filter.set.null.types:

Changing behaviour for Zend_Filter_Null
---------------------------------------

Sometimes it's not enough to filter based on ``empty()``. Therefor ``Zend_Filter_Null`` allows you to configure which type will be converted and which not.

The following types can be handled:

- **boolean**: Converts a boolean **FALSE** value to ``NULL``.

- **integer**: Converts an integer **0** value to ``NULL``.

- **empty_array**: Converts an empty **array** to ``NULL``.

- **float**: Converts an float **0.0** value to ``NULL``.

- **string**: Converts an empty string **''** to ``NULL``.

- **zero**: Converts a string containing the single character zero (**'0'**) to ``NULL``.

- **all**: Converts all above types to ``NULL``. (This is the default behavior.)

There are several ways to select which of the above types are filtered. You can give one or multiple types and add them, you can give an array, you can use constants, or you can give a textual string. See the following examples:

.. code-block:: php
   :linenos:

   // converts false to null
   $filter = new Zend_Filter_Null(Zend_Filter_Null::BOOLEAN);

   // converts false and 0 to null
   $filter = new Zend_Filter_Null(
       Zend_Filter_Null::BOOLEAN + Zend_Filter_Null::INTEGER
   );

   // converts false and 0 to null
   $filter = new Zend_Filter_Null( array(
       Zend_Filter_Null::BOOLEAN,
       Zend_Filter_Null::INTEGER
   ));

   // converts false and 0 to null
   $filter = new Zend_Filter_Null(array(
       'boolean',
       'integer',
   ));

You can also give an instance of ``Zend_Config`` to set the wished types. To set types afterwards use ``setType()``.


