Python Style Guide
==================

One memo for Python coding style.


Why
---

**Coding Style Matters.**

If you still do not take this seriously, google `why coding style matters 
<https://www.google.com.hk/search?q=why%20coding%20style%20matters>`_ or
ask anyone who is professional.


Code Layout
-----------

Use 4 spaces per indentation level, no tab.

Limit all lines to a maximum of 79 characters.

Seperate top-level definitions with two blank lines, definitions inside should
be separated by a single blank line.  Extra blank lines may be used if needed.

Source file should always use UTF-8 for encoding.

Imports should be grouped in the following order:
    
1. standard library imports
2. related third party imports
3. local application/library specific imports

Write docstrings for all modules, functions, classes, and methods.  All
docstrings should be formatted in reStructuredText as understood by Sphinx. 

.. code:: python

    # -*- coding: utf-8 -*-
    """
        Code Layout
        ~~~~~~~~~~~
    """
    import os
    import sys
    from subprocess import Popen, PIPE

    import requests

    from app import something
    

    # Surround binary operators with a single space on either side
    g = "global"


    def long_function_name(param_one, param_two,
                           param_three, param_four):
        """One demo for continuation lines.

        Continuation lines should align wrapped elements either vertically
        using Python's implicit line joining inside parentheses, brackets
        and braces or use backslashes, in which case you should align the
        next line with the last dot or equal sign or indent four spaces.
        """
        print(param_one)
        print(param_two)

        print(param_three)
        print(param_four)

        this_is_a_very_long(function_call, 'with many parameters') \
            .that_returns_an_object_with_an_attribute

        MyModel.query.filter(MyModel.scalar > 120) \
                     .order_by(MyModel.name.desc()) \
                     .limit(10)


    foo = long_function_name(var_one, var_two,
                             var_three, var_four)


    my_dict = {
        "key": "value",
        "key2": "value2"
    }


Naming Conventions
------------------

Modules and packages should have short, all-lowercase names, underscores can
be used if it improves readability.

Class names should use the CapWords convention.

Function names should be lowercase, with words separated by underscores as
necessary to improve readability.

Always use ``self`` for the first argument to instance methods.

Always use ``cls`` for the first argument to class methods.

Use one leading underscore only for non-public methods and instance variables.

Constants are usually defined on a module level and written in all capital
letters with underscores separating words.

.. code:: python
    
    # -*- coding: utf-8 -*-
    """
        Naming
        ~~~~~~
    """

    TOTAL_NUMBER = 100


    class FooDemo(object):
        """FooDemo.

        Used for class name convention demo.
        """

        def __init__(self, foo):
            self.foo = foo
            self._number = TOTAL_NUMBER

        @classmethod
        def name(cls):
            print(cls.__name__)

        def _double(self):
            return self._number * 2

        def get_number(self):
            return self._double()


Recommendations
---------------

Comparisons to singletons like ``None`` should always be done with ``is`` or
``is not``, never the equality operators.

Always use a ``def`` statement instead of an assignment statement that binds a
lambda expression directly to a name.

Derive exceptions from ``Exception`` rather than ``BaseException``.

When raising an exception, use ``raise ValueError('message')``.

When catching exceptions, mention specific exceptions whenever possible
instead of using a bare ``except:`` clause.

When a resource is local to a particular section of code, use a ``with``
statement to ensure it is cleaned up promptly and reliably after use.

Object type comparisons should always use ``isinstance()`` instead of comparing
types directly.

.. code:: python

    if foo is not None:
        pass

    # Do not use f = lambda x: 2 * x
    def f(x): return 2 * x

    class MyError(Exception):
        """My Error."""
        pass

    try:
        import platform_specific_module
    except ImportError:
        platform_specific_module = None


Source
------

Read the excellent code to learn more in the real world.

- `Flask <https://github.com/mitsuhiko/flask>`_
- `Werkzeug <https://github.com/mitsuhiko/werkzeug>`_


Links
-----

- `PEP 8 <http://legacy.python.org/dev/peps/pep-0008/>`_
- `Pocoo Style Guide <http://www.pocoo.org/internal/styleguide/>`_


Better
------

If you feel anything wrong, feedbacks or pull requests are welcomed.
