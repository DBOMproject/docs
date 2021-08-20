Query
=====

This page gives an overview on query format supported by DBoM

============
Query Syntax
============

Queries are expressed as JSON objects describing Fields to be queried along with optional operators for applying conditional logic.

Equality
--------

Equality can specified using the ``$eq`` operator

::

   "query": { 
      <field1>: 
      {
        "$eq":<value1>
      }
   }

AND
---

And can specified using the ``$and`` operator

::

   "query": 
   { 
      "$and": [
         { 
            <field1>: 
            {
               "$eq":<value1>
            }
         },
         { 
            <field2>: 
            {
               "$eq":<value2>
            }
         }
      ]
   }

OR
---

Or can specified using the ``$or`` operator

::
 
   "query": 
   { 
      "$or": [
         { 
            <field1>: 
            {
               "$eq":<value1>
            }
         },
         { 
            <field2>: 
            {
               "$eq":<value2>
            }
         }
      ]
   }

Nested Object
-------------

Nested fields can be searched using the ``$eq`` operator

::

   "query": { 
      <field1>: {
         "$eq": 
         {
           <subfield1>:<value1>,
           <subfield2>:<value2>,
         }
      }
   }

Nested Field
------------

Nested fields can be search using dot notation

::

   "query": { 
      "<field1>.<subfield1>":
      {
         "$eq":<value1>
      }
   }

Operators
---------

Operators are identified by the use of a dollar sign ($) prefix in the name field.

+-------------------------+-------------+-----------------------+--------------------------------------------------------------------+
|      Operator type      |  Operator   |       Argument        |                              Purpose                               |
+=========================+=============+=======================+====================================================================+
| :ref:`query:Comparison` | ``$lt``     | Any JSON              | Field is less than the argument                                    |
+-------------------------+-------------+-----------------------+--------------------------------------------------------------------+
| :ref:`query:Comparison` | ``$lte``    | Any JSON              | Field is less than or equal to the argument.                       |
+-------------------------+-------------+-----------------------+--------------------------------------------------------------------+
| :ref:`query:Comparison` | ``$eq``     | Any JSON              | Field is equal to the argument                                     |
+-------------------------+-------------+-----------------------+--------------------------------------------------------------------+
| :ref:`query:Comparison` | ``$ne``     | Any JSON              | Field is not equal to the argument.                                |
+-------------------------+-------------+-----------------------+--------------------------------------------------------------------+
| :ref:`query:Comparison` | ``$gte``    | Any JSON              | Field is greater than or equal to the argument.                    |
+-------------------------+-------------+-----------------------+--------------------------------------------------------------------+
| :ref:`query:Comparison` | ``$gt``     | Any JSON              | Field is greater than the to the argument.                         |
+-------------------------+-------------+-----------------------+--------------------------------------------------------------------+
| :ref:`query:Comparison` | ``$exists`` | Boolean               | Check whether field exists or not                                  |
+-------------------------+-------------+-----------------------+--------------------------------------------------------------------+
| :ref:`query:Logical`    | ``$and``    | Boolean               | All the selectors in the array match                               |
+-------------------------+-------------+-----------------------+--------------------------------------------------------------------+
| :ref:`query:Logical`    | ``$not``    | Boolean               | The given selector does not match.                                 |
+-------------------------+-------------+-----------------------+--------------------------------------------------------------------+
| :ref:`query:Logical`    | ``$nor``    | Boolean               | None of the selectors in the array match                           |
+-------------------------+-------------+-----------------------+--------------------------------------------------------------------+
| :ref:`query:Logical`    | ``$or``     | Boolean               | Any of the selectors in the array match.                           |
+-------------------------+-------------+-----------------------+--------------------------------------------------------------------+
| :ref:`query:Array`      | ``$in``     | Array of  JSON values | Field must exist in the list provided.                             |
+-------------------------+-------------+-----------------------+--------------------------------------------------------------------+
| :ref:`query:Array`      | ``$nin``    | Array of JSON values  | Field must not exist in the list provided.                         |
+-------------------------+-------------+-----------------------+--------------------------------------------------------------------+
| :ref:`query:Array`      | ``$all``    | Array of JSON values  | Array value if it contains all the elements of the argument array. |
+-------------------------+-------------+-----------------------+--------------------------------------------------------------------+
| :ref:`query:Regex`      | ``$regex``  | String                | Regular expression met by field                                    |
+-------------------------+-------------+-----------------------+--------------------------------------------------------------------+

Comparison
----------

Compares a field to a value

::

   "query": {
      <field1>: 
      {
        "$gt":<value1>
      }
   }

Logical
-------

Joins query clauses together

Find the :ref:`query:AND` and :ref:`query:OR` above

::

   "query": {
      "$not": 
      { 
         <field1>: 
         {
            "$eq":<value1>
         }
      }
   }

Array
-----

Checks for values in an array

::

   "query": {
      <field1>: 
      {
        "$in":[<value1>,<value2>]
      }
   }

Regex
-----

Check against `regex expressions <https://regexr.com/>`_

::

   "query": {
      <field1>: 
      {
        "$regex":<regex1>
      }
   }

=============
Filter Syntax
=============

Filters are expressed as an array of fields to be included in the response

::

   "query": { 
      <field1>: <value1>,
      <field2>: <value2>
   },
   "filter": [field1, field3]
