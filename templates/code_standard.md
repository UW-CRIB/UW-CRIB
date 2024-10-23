# CRIB Python Code Standard (WIP)

This code standard is built specifically for Python and takes heavy influence from the existing
PEP 8 standard.


## Table of Contents

* [Indentations](#indentations)
* [Max Line Length](#max_line_length)
* [Line Breaks for Binary Operators](#binary_op_line_breaks)
* [Blank Lines](#blank_lines)
* [Imports](#imports)
* [White Spaces in Expressions](#white_spaces)
* [Comments](#comments)


<h2 id="indentations">Indentations</h2>

Each new indentation level should be made up of 4 spaces.

Continuation lines should either be aligned vertically with the elements in the previous line or
gain an extra level of indentation to distinguish the arguments from the proceding code:

    # Aligned with elements in the previous line.
    def long_function_name(var_one, var_two, var_three,
                           var_four):
        print(var_one)

    # Extra level of indentation.
    def long_function_name(
            var_one, var_two, var_three, var_four):
        print(var_one)

The closing bracket of multiline contructs should line up with the first character of the line
that started the contruct:

    my_list = [
        1, 2, 3,
        4, 5, 6
    ]


<h2 id="max_line_length">Max Line Length</h2>

Limit all lines to a maximum of 99 characters.

limiting the length of lines improves readability as the entire line fits on screen and allows
multiple files to be displayed side by side.


<h2 id="binary_op_line_breaks">Line Breaks for Binary Operators</h2>

For multiline forumlas, the line should break immediately before the binary opoerator. This makes
it clear what operator is applied to each variable.

    total = (var_one
             + var_two
             + var_three 
             - var_four
             - var_five)


<h2 id="blank_lines">Blank Lines</h2>

Surround functions definitions outside of classes and class definitions with two blank lines
on both sides.

Surround Method definitions inside classes with one blank line on both sides.

Blank lines within function and method definitions should be limited to make it clear all the
code is related. Blank lines can be used to seperate different logical sections within a
function or method definition.


<h2 id="imports">Imports</h2>

Imports should be at the top of the file immediately proceding any module comments. Imports from
different libraries should be on seperate lines but it is okay to import multiple modules from the
same library on the same line.

    import pandas as pd
    from mylib import ClassOne, ClassTwo


<h2 id="white_spaces">White Spaces in Expressions</h2>

Avoid adding unnecisary whitespaces in expressions.

* Immediately after brakets:

        # Correct
        fun(var_one, var_two)
        # Incorrect
        fun( var_one, var_two )

* Immediately before commas, semicolons, or colons:

        # Correct
        if true: x = y
        # Incorrect
        if true : x = y

* Immediately before open parenthesis that start an argument list:

        # Correct
        fun(var_one)
        # Incorrect
        fun (var_one)

* Immediately before indexing or slicing open parenthesis:

        # Correct
        list[1]
        # Incorrect
        list [0]

* More than one space around assignments:

        # Correct
        var_one = 1
        var_two = 2
        var_three = 3

        # Incorrect
        var_one   = 1
        var_two   = 2
        var_three = 3

<h2 id="comments">Comments</h2>

* comments at the top of each file
* comments in the code that describe classes/objects immediately before them