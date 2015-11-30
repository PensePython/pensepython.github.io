Variables, expressions and statements
=====================================

One of the most powerful features of a programming language is the
ability to manipulate **variables**. A variable is a name that refers to
a value.

Assignment statements
---------------------

An **assignment statement** creates a new variable and gives it a value:

::

    >>> message = 'And now for something completely different'
    >>> n = 17
    >>> pi = 3.141592653589793

This example makes three assignments. The first assigns a string to a
new variable named message; the second gives the integer 17 to n; the
third assigns the (approximate) value of :math:`\pi` to pi.

A common way to represent variables on paper is to write the name with
an arrow pointing to its value. This kind of figure is called a **state
diagram** because it shows what state each of the variables is in (think
of it as the variable’s state of mind). Figure [fig.state2] shows the
result of the previous example.

.. figure:: figs/state2.pdf
   :alt: State diagram.

   State diagram.

Variable names
--------------

Programmers generally choose names for their variables that are
meaningful—they document what the variable is used for.

Variable names can be as long as you like. They can contain both letters
and numbers, but they can’t begin with a number. It is legal to use
uppercase letters, but it is conventional to use only lower case for
variables names.

The underscore character, ``_``, can appear in a name. It is often used
in names with multiple words, such as ``your_name`` or
``airspeed_of_unladen_swallow``.

If you give a variable an illegal name, you get a syntax error:

::

    >>> 76trombones = 'big parade'
    SyntaxError: invalid syntax
    >>> more@ = 1000000
    SyntaxError: invalid syntax
    >>> class = 'Advanced Theoretical Zymurgy'
    SyntaxError: invalid syntax

76trombones is illegal because it begins with a number. more@ is illegal
because it contains an illegal character, @. But what’s wrong with
class?

It turns out that class is one of Python’s **keywords**. The interpreter
uses keywords to recognize the structure of the program, and they cannot
be used as variable names.

Python 3 has these keywords:

::

    False      class      finally    is         return
    None       continue   for        lambda     try
    True       def        from       nonlocal   while
    and        del        global     not        with
    as         elif       if         or         yield
    assert     else       import     pass
    break      except     in         raise

You don’t have to memorize this list. In most development environments,
keywords are displayed in a different color; if you try to use one as a
variable name, you’ll know.

Expressions and statements
--------------------------

An **expression** is a combination of values, variables, and operators.
A value all by itself is considered an expression, and so is a variable,
so the following are all legal expressions:

::

    >>> 42
    42
    >>> n
    17
    >>> n + 25
    42

When you type an expression at the prompt, the interpreter **evaluates**
it, which means that it finds the value of the expression. In this
example, n has the value 17 and n + 25 has the value 42.

A **statement** is a unit of code that has an effect, like creating a
variable or displaying a value.

::

    >>> n = 17
    >>> print(n)

The first line is an assignment statement that gives a value to n. The
second line is a print statement that displays the value of n.

When you type a statement, the interpreter **executes** it, which means
that it does whatever the statement says. In general, statements don’t
have values.

Script mode
-----------

So far we have run Python in **interactive mode**, which means that you
interact directly with the interpreter. Interactive mode is a good way
to get started, but if you are working with more than a few lines of
code, it can be clumsy.

The alternative is to save code in a file called a **script** and then
run the interpreter in **script mode** to execute the script. By
convention, Python scripts have names that end with .py.

If you know how to create and run a script on your computer, you are
ready to go. Otherwise I recommend using PythonAnywhere again. I have
posted instructions for running in script mode at
http://tinyurl.com/thinkpython2e.

Because Python provides both modes, you can test bits of code in
interactive mode before you put them in a script. But there are
differences between interactive mode and script mode that can be
confusing.

For example, if you are using Python as a calculator, you might type

::

    >>> miles = 26.2
    >>> miles * 1.61
    42.182

The first line assigns a value to miles, but it has no visible effect.
The second line is an expression, so the interpreter evaluates it and
displays the result. It turns out that a marathon is about 42
kilometers.

But if you type the same code into a script and run it, you get no
output at all. In script mode an expression, all by itself, has no
visible effect. Python actually evaluates the expression, but it doesn’t
display the value unless you tell it to:

::

    miles = 26.2
    print(miles * 1.61)

This behavior can be confusing at first.

A script usually contains a sequence of statements. If there is more
than one statement, the results appear one at a time as the statements
execute.

For example, the script

::

    print(1)
    x = 2
    print(x)

produces the output

::

    1
    2

The assignment statement produces no output.

To check your understanding, type the following statements in the Python
interpreter and see what they do:

::

    5
    x = 5
    x + 1

Now put the same statements in a script and run it. What is the output?
Modify the script by transforming each expression into a print statement
and then run it again.

Order of operations
-------------------

When an expression contains more than one operator, the order of
evaluation depends on the **order of operations**. For mathematical
operators, Python follows mathematical convention. The acronym
**PEMDAS** is a useful way to remember the rules:

-  **P**\ arentheses have the highest precedence and can be used to
   force an expression to evaluate in the order you want. Since
   expressions in parentheses are evaluated first, 2 \* (3-1) is 4, and
   (1+1)\*\*(5-2) is 8. You can also use parentheses to make an
   expression easier to read, as in (minute \* 100) / 60, even if it
   doesn’t change the result.

-  **E**\ xponentiation has the next highest precedence, so 1 + 2\*\*3
   is 9, not 27, and 2 \* 3\*\*2 is 18, not 36.

-  **M**\ ultiplication and **D**\ ivision have higher precedence than
   **A**\ ddition and **S**\ ubtraction. So 2\*3-1 is 5, not 4, and
   6+4/2 is 8, not 5.

-  Operators with the same precedence are evaluated from left to right
   (except exponentiation). So in the expression degrees / 2 \* pi, the
   division happens first and the result is multiplied by pi. To divide
   by :math:`2 \pi`, you can use parentheses or write degrees / 2 / pi.

I don’t work very hard to remember the precedence of operators. If I
can’t tell by looking at the expression, I use parentheses to make it
obvious.

String operations
-----------------

In general, you can’t perform mathematical operations on strings, even
if the strings look like numbers, so the following are illegal:

::

    '2'-'1'    'eggs'/'easy'    'third'*'a charm'

But there are two exceptions, + and .

The + operator performs **string concatenation**, which means it joins
the strings by linking them end-to-end. For example:

::

    >>> first = 'throat'
    >>> second = 'warbler'
    >>> first + second
    throatwarbler

The operator also works on strings; it performs repetition. For example,
``'Spam'*3`` is ``'SpamSpamSpam'``. If one of the values is a string,
the other has to be an integer.

This use of + and makes sense by analogy with addition and
multiplication. Just as 4\*3 is equivalent to 4+4+4, we expect
``'Spam'*3`` to be the same as ``'Spam'+'Spam'+'Spam'``, and it is. On
the other hand, there is a significant way in which string concatenation
and repetition are different from integer addition and multiplication.
Can you think of a property that addition has that string concatenation
does not?

Comments
--------

As programs get bigger and more complicated, they get more difficult to
read. Formal languages are dense, and it is often difficult to look at a
piece of code and figure out what it is doing, or why.

For this reason, it is a good idea to add notes to your programs to
explain in natural language what the program is doing. These notes are
called **comments**, and they start with the ``#`` symbol:

::

    # compute the percentage of the hour that has elapsed
    percentage = (minute * 100) / 60

In this case, the comment appears on a line by itself. You can also put
comments at the end of a line:

::

    percentage = (minute * 100) / 60     # percentage of an hour

Everything from the # to the end of the line is ignored—it has no effect
on the execution of the program.

Comments are most useful when they document non-obvious features of the
code. It is reasonable to assume that the reader can figure out *what*
the code does; it is more useful to explain *why*.

This comment is redundant with the code and useless:

::

    v = 5     # assign 5 to v

This comment contains useful information that is not in the code:

::

    v = 5     # velocity in meters/second.

Good variable names can reduce the need for comments, but long names can
make complex expressions hard to read, so there is a tradeoff.

Debugging
---------

Three kinds of errors can occur in a program: syntax errors, runtime
errors, and semantic errors. It is useful to distinguish between them in
order to track them down more quickly.

Syntax error:
    “Syntax” refers to the structure of a program and the rules about
    that structure. For example, parentheses have to come in matching
    pairs, so (1 + 2) is legal, but 8) is a **syntax error**.

    If there is a syntax error anywhere in your program, Python displays
    an error message and quits, and you will not be able to run the
    program. During the first few weeks of your programming career, you
    might spend a lot of time tracking down syntax errors. As you gain
    experience, you will make fewer errors and find them faster.

Runtime error:
    The second type of error is a runtime error, so called because the
    error does not appear until after the program has started running.
    These errors are also called **exceptions** because they usually
    indicate that something exceptional (and bad) has happened.

    Runtime errors are rare in the simple programs you will see in the
    first few chapters, so it might be a while before you encounter one.

Semantic error:
    The third type of error is “semantic”, which means related to
    meaning. If there is a semantic error in your program, it will run
    without generating error messages, but it will not do the right
    thing. It will do something else. Specifically, it will do what you
    told it to do.

    Identifying semantic errors can be tricky because it requires you to
    work backward by looking at the output of the program and trying to
    figure out what it is doing.


.. _glossary02:

Glossary
--------

.. include:: glossary/02.txt


Exercises
---------

Repeating my advice from the previous chapter, whenever you learn a new
feature, you should try it out in interactive mode and make errors on
purpose to see what goes wrong.

-  We’ve seen that n = 42 is legal. What about 42 = n?

-  How about x = y = 1?

-  In some languages every statement ends with a semi-colon, ;. What
   happens if you put a semi-colon at the end of a Python statement?

-  What if you put a period at the end of a statement?

-  In math notation you can multiply :math:`x` and :math:`y` like this:
   :math:`x y`. What happens if you try that in Python?

Practice using the Python interpreter as a calculator:

#. The volume of a sphere with radius :math:`r` is
   :math:`\frac{4}{3} \pi r^3`. What is the volume of a sphere with
   radius 5?

#. Suppose the cover price of a book is $24.95, but bookstores get a 40%
   discount. Shipping costs $3 for the first copy and 75 cents for each
   additional copy. What is the total wholesale cost for 60 copies?

#. If I leave my house at 6:52 am and run 1 mile at an easy pace (8:15
   per mile), then 3 miles at tempo (7:12 per mile) and 1 mile at easy
   pace again, what time do I get home for breakfast?
