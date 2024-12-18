============================
Intermediate Representations
============================

An input program in the source language may go through many intermediate representations within
a compiler before it is in a form ready for execution. 
  
One of the first such intermediate representations that we have seen is the
the Abstract Syntax Tree (AST), which is mainly concerned with the grammar of the source language. 

From the AST, we generate a different kind of intermediate representation, one that is more amenable 
to the manipulations required during optimization and execution. There are many such representations; we will 
limit ourselves to the following.

* Stack based IR
* Register based IR
* Sea of Nodes IR

Stack-Based IR
==============

The stack based IR encodes stack operations as part of the intermediate representation. Lets look at a simple 
example::

   func foo(n: Int)->Int {
      return n+1;
   }
   
Produces::

   L0:
	   load 0
	   pushi 1
	   addi
	   jump L1
   L1:

The stack based IR is so called because many of the intructions in the IR push values to an evaluation stack at 
runtime. Above for example we have the following instructions:

* ``load 0`` - this refers to loading the value of the input parameter ``n`` to the stack.
* ``pushi 1`` - pushes the constant ``1`` to the stack.
* ``addi`` - pops the two topmost values on the stack, and computes the sum and pushes this to the stack

So at the end of the program we are left with the sum of ``n+1`` on the stack, and this forms the return 
value of the function.

Advantages
----------
* The IR is compact to represent in stored form, hence many languages choose to encode their compiled code in
  this form. Examples are Java, C#, Web Assembly.
* The IR can be executed easily by an Interpreter.

Disadvantages
-------------
* Not easy to implement optimizations
* Harder to analyze the IR, although there are methods available to do so.

Examples
--------
* Example implementation on EeZee Programming Language
* Java Specifications
* Approaches for Analysis

Register Based IR
=================





