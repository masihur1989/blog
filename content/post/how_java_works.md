---
title: "How Java Works"
date: 2022-11-09T20:32:50-05:00
categories: [development, publishing]
tags: [hugo,content,static site generator]
draft: false
---
This is the first of a series of blogs I will write in Java. Today I will discuss How Java Works. This is an optional blog, if anyone is interested to know java more, you can go over it.

First we need to understand some concepts.

A high-level (also called third-generation) programming languages allow you to write programs in a language similar to natural language, in other word Human readable. The high-level program is called the source code.

A low-level programming language is something closer to what makes sense to a computer. All high-level program needs to be converted into low-level language.

Compilers, most computer languages use the “compile-link-execute” format. You start with source code and the compiler converts this program into a low-level program.

In most compiled languages, the file containing the resulting low-level code is called an object file. A collection of object files are linked together to create an executable file (i.e., the operating system can load the executable file into RAM to run the program). Another term for an executable is “(relocatable) machine code”.

The process of linking connects the object files that you have created along with other pre-existing object files to form an executable file. The linker does this job. You shouldn’t expect to find link errors until you’re writing larger programs that have multiple parts; link errors occur when the object files for your program don’t completely communicate appropriately.

Interpreters, an interpreted language takes each high-level statement, determines its low-level version and executes (while linking if needed) the result. This is done for each statement in succession (before the next high-level statement is even looked at).

As an analogy you can think of a foreign language, a compiler acts as a translator and an interpreter acts as the name suggests, an interpreter.

The way Java works, Java is a language which is neither truly interpreted nor compiled; instead, a combination of the two forms is used. This method has advantages which were not present in earlier languages.

Platform Independency, to understand the primary advantage of Java, you’ll have to learn about platforms. In most programming languages, a compiler (or interpreter) generates code that can execute on a specific target machine. For example, if you compile a C/C++ program on a Windows machine, the executable file can be copied to any other machine but it will only run on other Windows machines but never another machine (e.g., a Mac or a Linux machine). A platform is determined by the target machine (along with its operating system). For earlier languages, language designers needed to create a specialized version of the compiler (or interpreter) for every platform. If you wrote a program that you wanted to make available on multiple platforms, you, as the programmer, would have to do quite a bit of additional work. You would have to create multiple versions of your source code for each platform.

Java succeeded in eliminating the platform issue for high-level programmers because it has reorganized the compile-link-execute sequence at an underlying level of the compiler. Details are complicated but, essentially, the designers of the Java language isolated those programming issues which are dependent on the platform and developed low-level means to abstractly refer to these issues. Consequently, the Java compiler doesn’t create an object file, but instead it creates a bytecode file which is, essentially, an object file for a virtual machine. In fact, the Java compiler is often called the JVM compiler (for Java Virtual Machine).

Consequently, you can write a Java program (on any platform) and use the JVM compiler (called javac) to generate a bytecode file with the extension .class. This byte code file can be used on any platform (that has installed Java). However, byte code is not an executable file. To execute a byte code file, you actually need to invoke a Java interpreter (called java). Every platform has its own Java interpreter which will automatically address the platform-specific issues that can no longer be put off. When platform-specific operations are required by the bytecode, the Java interpreter links in appropriate code specific to the platform.

To summarize how Java works (to achieve platform independence), think about the compile-link-execute cycle. In earlier programming languages, the cycle is more closely defined as “compile-link then execute”. In Java, the cycle is closer to “compile then link-execute”.
