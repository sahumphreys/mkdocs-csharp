---
title: Some background on the C# language
---

# {{ title }}

## A Brief History

C# is a modern, general-purpose, object-oriented, high-level programming language. Its syntax is similar to both C and C++, but it is designed to be easier to use than either of those languages. C# was developed in 2000 by Anders Hejlsberg as a direct competitor to Java. Anders also created Turbo Pascal and was the chief architect behind Delphi.

Each C# program consists of one or more files with the `.cs` extension. These files are combined by the compiler to create an executable file.

## The .NET Framework

C# is part of the __.NET Framework__, which also includes other languages like VB.NET, F#, and C++. The .NET Framework provides a vast collection of libraries and data types that are shared across these different languages.

At the core of the .NET Framework is the __Common Language Runtime (CLR)__, which is responsible for executing .NET programs. When you write code in C# (or another .NET language), it is first compiled into an intermediate form called the __Common Intermediate Language (CIL)__. This intermediate code is then managed and executed by the CLR.

This process is similar to how Java works, where source code is compiled into __bytecode__. However, C# takes this a step further by linking the intermediate code with the necessary libraries to create a program that can run efficiently on the target machine. While the compiled code is fast and efficient, it is still platform-independent because it needs to be recompiled to run on different operating systems.

!!! note "From the syllabus"
    **AQA**: Understand why an intermediate language such as bytecode is produced (3.6.3.1/4.6.3.1).
    
    - **Bytecode** is program code compiled from source code into an intermediate language that is designed for a software interpreter.

If this seems a bit complex, don’t worry. Most of this happens "under the hood," but it’s useful to have a basic understanding of the compilation process.

## .NET Framework vs .NET Core

You might encounter both __.NET Framework__ and __.NET Core__. In short, .NET Core is the open-source, cross-platform successor to .NET Framework. It is more versatile and designed to run on different operating systems. However, we will be using the .NET Framework by default in this course, as it is simpler to set up and use on Windows.

## Can I Use Another IDE?

While we recommend using Visual Studio or VSCode for this course, you can write and compile your C# programs without these IDEs as long as the .NET Framework is installed on your computer. There are resources online that explain how to do this, but since the IDE makes the process much easier, we suggest sticking with it, especially as you’re learning the basics.
