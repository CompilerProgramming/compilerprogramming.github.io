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
While this is true, they do cover various aspects of a compiler backend such as intermediate representations and
optimization techniques including peephole optimization, data flow analysis, register allocation etc.
I found the description of the lattice in a data flow analysis quite accessible. 

The 2nd edition adopts a more mathematical presentation style, whereas the earlier editions present
algorithms using pseudo code. I think the 1986 edition is the best.

The dragon books are a bit dated in that newer techniques such as Static Single Assignment or Graph 
Coloring Register Allocation etc. are not covered in any detail. I would even say that these books are not 
useful if your goal is to work with SSA IR. 

For a different take on 2nd edition see `Review of the second addition of the "Dragon Book" <https://gcc.gnu.org/wiki/Review_of_the_second_addition_of_the_Dragon_Book.>`_.

Engineering a Compiler, 2nd Ed. Cooper & Torczon. 2012.
=======================================================
This is a more modern version of the Dragon book. It is less focused on the lexical analysis / parsing
phases, and covers the later phases of a compiler in more detail. Exposition is similar to the Dragon book, i.e. describes
techniques conceptually, and some algorithms are described in detail using a form of pseudo code.

Defines an intermediate language called ILOC, but this does not have support for function calls.

In practice, I found this book helful when implementing Dominator algorithm and SSA transformation. However, it left out
important parts in its coverage of SSA which meant that the algorithms as described do not work. For instance:

* The SSA construction algorithm inserts Phis in blocks where the original variable is dead (semi-pruned SSA). This then
  causes the renaming phase to fail as there is no available definition of the variable.
* Liveness analysis does not cover SSA form and does not handle phis correctly.
* Exiting out of SSA is described conceptually but the algorithms are not
  described in detail. 

In practice though it is easy to recommend Engineering a Compiler over the Dragon books.

Both this and the Dragon books describe ahead of time compilers and cover topics that are suited for procedural languages
such as C or traditional Pascal or Fortran. They cover both front-end and back-end techniques; however, on the front-end
side, interesting topics such as Object Orientation, Closures, Generics, Semantic analysis of more complex languages 
such as Java are not covered.

Modern Compiler Implementation in C. Appel. 1998. (Tiger book)
==============================================================
This book takes a hands on tutorial like approach to describing how to implement both the front-end and back-end 
of a compiler, using a toy language called Tiger as an example. Algorithms are described in pseudo code. 
If I had to choose from the Dragon book, Engineering a compiler, and this book, I would pick this one and 
Engineering a Compiler.

It covers a lot of techniques, and usually presents algorithms in pseudo code form. I consulted this book
when implementing SSA and SCCP, but the descriptions were not sufficiently comprehensive so that I had to 
consult other material too.

This book covers functional languages, closures, as well as Object Oriented languages such as Java. Type inference is 
covered too.

Crafting a Compiler. Fischer, LeBlanc, Cytron. 2010.
====================================================
The last couple of chapters are the most interesting - these focus on code generation and program optimization. 

The 2nd edition of the book (with Cytron as co author) has a description of Static Single assignment. However the
description is based on a statement level IR, rather than one that uses Basic Blocks. Also, the algorithm for exiting
SSA is not described. 

The 1st edition describes data flow analysis in more detail, but does not cover SSA.

Apart from the final two chapters, the rest of the book is about parsing and semantic analysis.

Building an Optimizing Compiler. Bob Morgan. 1998.
==================================================
I have the kindle edition which is very poor and hard to read. I wish I had a paper copy.

This book is almost completely about the backend of the compiler. I consulted the description of SCCP and
based my implementation at least in part on the descriptions. In particular I found some discussion about how to
exploit local knowledge in conditional branches to handle null checks, which was useful, and not discussed in
other books.

Advanced Compiler Design & Implementation. Muchnick. 1997.
==========================================================
I have the kindle edition, which is very poor quality and hard to read.

This book is mostly about the backend of a compiler, focusing on optimization.

My impression is that this book describes many algorithms in detail. But when I tried to implement one of the
simpler algorithms (18.1 Unreachable Code Elimination) I found that the description left out a 
part (No_Path) of the algorithm.

This book describes the idea of multiple levels of intermediate representation, HIR, MIR and LIR.
I guess this has influenced many compiler implementations.

Its coverage of SSA is rudimentary - I guess it was written when SSA was still very new. Hence if you are
working with SSA IR then you will need to consult other material.

The Graph Coloring register allocation algorithm is presented in detail and is based on the paper by
Preston Briggs.

This book has a reputation of containing many errors, although I assume the latest printings have the errors
fixed.

Despite its faults, it is a must have book if you want to learn about compiler construction.

Retargetable C Compiler, A: Design and Implementation. Hanson & Fraser. 1995.
=============================================================================
Describes a production C compiler. Detailed dsecription of the actual compiler code.

Weak on theoretical aspects, and limited by features of the compiler being described. The compiler
implementation is a single pass code generator, hence its optimizing capabilities are limited.
There is no coverage of data flow analysis or SSA as these weren't used by the implementation.

In short this describes an old school C compiler that generates code fast, but lacks optimizations.

Program Flow Analysis: Theory and Applications. Editors Muchnick, Jones. 1981.
==============================================================================
Collection of essays on program analysis, by various authors. This is pre-SSA, hence a bit
dated.

SSA-Based Compiler Design - various authors
===========================================
An online version of this book is available `here <https://pfalcon.github.io/ssabook/latest/book-full.pdf>`_.
This book is a collection of articles on various topics related to SSA. As such it presents more
recent knowledge regarding SSA construction, optimizations based on SSA, and finally destruction and 
register allocation.

Other Book Reviews
==================
* `List of compiler books <https://gcc.gnu.org/wiki/ListOfCompilerBooks>`_
