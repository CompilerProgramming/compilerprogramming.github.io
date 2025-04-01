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

In this IR, control flow can be represented either using labels and branching instructions, or by grouping 
instructions into basic blocks, and linking basic blocks through jump instructions. These two approaches are
are quite similar, you can think of a label as indicating the start of a basic block, and a jump as ending
a basic block.

The idea is that inside a basic block, instructions are supposed to execute linearly one after the other.
Each basic block ends with a branching instruction, something like a goto or a conditional jump.

Here is a simple example of input source code and the IR you might see::

   func foo()->Int
   {
      return 1 == 1 && 2 == 2
   }

This results in IR that may look like this::

   L0:
	   pushi 1
	   pushi 1
	   eq
	   cbr L2 L3
   L2:
	   pushi 2
	   pushi 2
	   eq
	   jump L4
   L3:
	   pushi 0
	   jump L4
   L4:
	   jump L1
   L1:

Each basic block begins with a label, which is just the unique name of the block.

* The ``jump`` instruction transfers control from a basic block to another.
* The ``cbr`` instruction is the conditional branch. It consumes the top most value from the stack, 
  and if this value is true, then control is transferred to the first block, else to the second block.
* The ``eq`` instruction compares two values on top of the stack, and replaces them with integer value
  ``1`` or ``0``.

Advantages
----------
* The IR is compact to represent in stored form, hence many languages choose to encode their compiled code in
  this form. Examples are Java, C#, Web Assembly.
* The IR can be executed easily by an Interpreter.
* Relatively easy to generate from an AST.

Disadvantages
-------------
* Not easy to implement optimizations
* Harder to analyze the IR, although there are methods available to do so.

Examples
--------
* Example implementation in EeZee Programming Language
* Java Specifications
* Web Assembly Specifications

Register Based IR or Three-Address IR
=====================================

This intermediate representation uses named slots called virtual registers in the Instruction when referencing
values. Lets look at the same example we saw above::

   func foo(n: Int)->Int {
      return n+1;
   }
   
Produces::

   L0:
      %t1 = n+1
      ret %t1
      goto  L1
   L1:

The instructions above are as follows:

* `%t1 = n+1` - is a typical three-address instruction of the form `result = value1 operator value2`. The name `%t1` 
  refers to a temporary, whereas `n` refers to the input argument `n`.
* `ret %t1` - is the return instruction, in this instance it references the temporary.

The virtual registers in the IR are so called because they do not map to real registers in the target physical machine.
Instead these are just named slots in the abstract machine responsible for executing the IR. Typically, the abstract machine
will assign  each virtual register a unique location in its stack frame. So we still end up using the function's
stack frame, but the IR references locations within the stack frame via these virtual names, rather than implicitly
through push and pop instructions.

Control flow is represented the same way as for the stack IR. Revisting the same example from above, we get following 
IR::

   L0:
      %t0 = 1==1
      if %t0 goto L2 else goto L3
   L2:
      %t0 = 2==2
      goto  L4
   L3:
      %t0 = 0
      goto  L4
   L4:
      ret %t0
      goto  L1
   L1:


Advantages
----------
* Readability: the flow of values is easier to trace, whereas with a stack IR you need to maintain a stack somewhere
* The IR can be executed easily by an Interpreter.
* Most optimization algorithms can be applied to this form of IR.

Disadvantages
-------------
* Each instruction has operands, hence representing the IR in serialized form takes more space.
* Harder to generate the IR during compilation. We will look in detail one way of generating this IR.

Examples
--------
* Example implementation in EeZee Programming Language
* LLVM instruction set
* Android Dalvik IR

Sea of Nodes IR
===============
