================
Lexical Analysis
================

When compiling a program we need to recognize the words and punctuations that make up the vocabulary of the language.
This part of the compiler is therefore known as "lexical" analysis.

Usually a compiler is given one or more input programs, and the first thing it must do is read the program and 
figure out what lexical elements appear in the program.

Typically, these lexical elements are known as tokens. So for example, in the following snippet of code::

    print('hi')

We have a number of lexical elements / tokens:

* ``print``
* ``(``
* ``'hi'``
* ``)``

There are many different ways to implement a "lexer" - the name we give to this component of the compiler.

* We can write this code by hand. This involves scanning the input program character by character and 
  deciding what tokens appear in the program.
* Or we can specify the lexical elements in a grammar and have a tool generate the code to process the input
  program and give us the tokens that appear in the program.

A lexical analyser can be designed to process input on demand, or it may be designed to translate the entire
input source to a set of tokens at the very beginning.

Considerations
==============

* Should comments in the input program be retained as tokens? Usually a lexer will discard comments, but in languages that
  allow comments to be retained as documentation, the lexer must not discard them.
* Should end of line markers be retained? Typically lexers drop all intermediate space including line markers,
  but if the language syntax depends on line markers then these may need to be retained.
* Should tokens copy the input text, convert them to another form, or retain pointers to the input itself?
  Retaining the original form of the lexical token may be important in some cases, for example if the lexer
  is used in a code formatter.
* How much can we peek ahead? During later stages of the compiler, depending on the complexity of the language grammar,
  it may be necessary to allow the compiler to look ahead one or more tokens without consuming them.
* Ancillary information regarding tokens such a line number, column number in the input source are invaluable for
  error reporting.

Example Hand-Coded Implementation
=================================

The `Lexer <https://github.com/CompilerProgramming/ez-lang/tree/main/lexer>`_ module in the EZ language
implementation contains an example of hand-coded lexical analyser written in Java. This implementation returns tokens
on demand. 

Another example is the `Lua lexer <https://lua.org/source/5.4/llex.c.html>`_.

