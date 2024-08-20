Implementation Language
=======================

A compiler can be implemented in any language we choose. For a pedagogical project it is more convenient
to choose a language that is widely used, has garbage collection, and comes with excellent tools such 
as IDEs and Debuggers.

Production quality compilers are often written in C, C++ or Rust. For us these languages are too difficult
to work with.

Lisp and Python appear to be popular languages in teaching projects. Lisp is not as widely used
as we would like our implementation language to be, and dynamically typed languages such as Python are 
harder to work with as the project grows.

Compared to C, C++ and Rust, the programming language D appears to be much more suitable for this project,
from a technical standpoint, that is. It is a garbage collection language that has less friction and is pleasant to 
work with. The main negatives are that it is not a popular language, and the tooling is not up to 
the standards of other languages.

Go would be a good candidate except that its an opinionated language that forces a certain programming model,
whereas we would like a language that offers least resistance.

Java and C# seem like good candidates. Java has some limitations that make it harder to write memory optimized
code that is often necessary in a production compiler, but we don't care so much about that. Between the two,
Java is both more popular and has a wider set of tools available.

I see no other sane choice but Java. My first choice would have been D if it was purely a technical question.
