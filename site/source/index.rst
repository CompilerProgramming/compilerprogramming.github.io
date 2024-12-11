================================
Welcome to Compiler Programming!
================================

This site aims to bring together practical knowledge regarding the design and implementation of optimizing compilers
and interpreters for Programming Languages. 

There are a number of books on Compilers and Interpreters however only a very few of them are accompanied by
source code that implements the topics covered by the book. See below for a list of useful 
learning projects that do include source code.

In recent years, thanks to LLVM, new programming language design has become a fertile space. New Language implementations
tend to focus on the language front-end, leveraging LLVM as the back-end for code optimization and code generation. 
While this is beneficial if you only care about the language design aspects, it is unhelpful for the industry 
as a whole, because the back-end of an optimizing compiler is a very interesting component, with a rich history of 
algorithms and data structures, and is a subject worthy of study on its own.

We will cover both front-end and back-end techniques. We will implement a small scale language as a way
to learn various techniques, see what the common challenges are and how to address them.
Language design not being our goal, we will keep the language as simple as possible so that it allows us to
focus on important implementation issues.

Initially we will start with a procedural language. Later we will add features such as closures from functional languages 
and classes and objects from OOP languages. We will also look at advanced front end techniques such as type inference and
generics.

The language will be statically typed to start with because this allows us to investigate the traditional compiler
optimization pipeline. Dyamically typed languages have their own interesting engineering problems.
We will eventually look at gradual typing and dynamic typing.

Implementation and Discussions
==============================

* The `EeZee programming language implementation <https://github.com/CompilerProgramming/ez-lang>`_ will serve as the playground for exploring various compilation
  techniques.
* This site is `maintained in github <https://github.com/CompilerProgramming/compilerprogramming.github.io/tree/dev>`_ too, and is generated using Sphinx.
* We have a `Discussion Forum <https://github.com/orgs/CompilerProgramming/discussions>`_.

Preliminaries
=============

.. toctree::
   :maxdepth: 1
   :caption: Preliminaries

   prelim-impl-lang

Basic Front-End techniques
==========================

.. toctree::
   :maxdepth: 1
   :caption: Parsing Techniques

   lexical-analysis
   syntax-analysis
   abstract-syntax-tree
   type-systems
   semantic-analysis

Basic Back-end techniques
=========================

* Stack based vs register based Intermediate Representation
* Control flow graphs and Basic Blocks
* Bytecode VM with simple garbage collection

Basic Optimization techniques
=============================

* Dominators and Control Flow Graph
* Static Single Assignment
* Data Flow Analysis, Type Lattices, Abstract Interpretation
* Peephole Optimizations
* Sea of Nodes Representation
* Code generation and Register Allocation

Language Tools
==============

* Debuggers 
* Language IDEs

Advanced Front-end techniques
=============================

* Type inference
* Classes and objects
* Closures
* Exception handling
* Gradual typing
* Generics


Some Useful Learning Resources
==============================

.. toctree::
   :maxdepth: 2
   :caption: Learning Resources

   learning-resources

Book Reviews
============

.. toctree::
   :maxdepth: 2
   :caption: Reviews

   compiler-books

Compiler Jobs
=============

* A listing of `compiler, language and runtime teams <https://github.com/mgaudet/CompilerJobs>`_ for people looking for compiler jobs.