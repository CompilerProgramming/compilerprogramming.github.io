==============
Compiler Books
==============

I own a bunch of compiler books that I have purchased over the years.

Dragon Books
============
I have 3 editions of these. 

* Principles of Compiler Design. Aho & Ullman, 1977.
* Compilers: Principles, Techniques and Tools. Aho, Sethi, Ullman, 1986.
* Compilers: Principles, Techniques and Tools, 2nd Ed. Aho, Lam, Sethi, Ullman, 2006.

These books are criticised today because of the excessive focus on lexical analysis and parsing techniques.
While this is true, they do cover various aspects of the compiler such as intermediate representation and
optimization techniques such as peephole optimzation,  data flow analysis, register allocation etc.

The 2nd edition adopts a more mathematical presentation style, whereas the earlier editions present
algorithms using pseudo code. I think the 1986 edition is the best.

For a different take on 2nd edition see `Review of the second addition of the "Dragon Book" <https://gcc.gnu.org/wiki/Review_of_the_second_addition_of_the_Dragon_Book.>`_.

Engineering a Compiler, 2nd Ed. Cooper & Torczon. 2012.
=======================================================
This is a more modern version of the Dragon book, one could say. Its less focused on the lexical analysis / parsing
phases, and covers later phases in more detail. Exposition is similar to the Dragon book, mostly describes
techniques conceptually, with some high level algorithm descriptions, but like the Dragon book, does not 
go into detailed descriptions of algorithms in general. 

Both this and the Dragon books describe ahead of time compilers and cover topics that are suited for procedural languages
such as C or traditional Pascal or Fortran. Interesting topics such as Object Orientation, Closures, Generics, 
or Semantic analysis of languages without forward declarations, etc. are not covered in any detail.

Modern Compiler Implementation in C. Appel. 1998.
=================================================
This book takes a more hands on approach to describing how to implement both a front end and back end of a compiler, 
using a toy language called Tiger as an example. Algorithms are described in pseudo code in more detail. If I had to choose
between the Dragon book, Engineering a compiler, and this book, I would pick this one.



Other Book Reviews
==================
* `List of compiler books <https://gcc.gnu.org/wiki/ListOfCompilerBooks>`_
