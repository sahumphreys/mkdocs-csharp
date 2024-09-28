---
title: Preface
---

# Preface

The aim of this text is to introduce both the general principles of programming in C\# and cover some of the theory behind introductory computer science.  The target audience are students studying A Level Computer Science who are either learning a new language[^1] or starting to program for the first time, no prior knowledge is assumed.  Included in the text are references to an A Level specification in the UK but these can be ignored for self-learners.  

The catalyst for writing this text arose when the author took on a new job that required teaching C\#.  Some fresh learning had to take place, trying out of examples, application of previously known concepts and constructs from other languages but applied to a new platform.  Lots of notes were made, lots of programs written to test out the new concepts and many questions asked.  The bulk of this text is drawn from those notes and from my colleagues as [Hills Road Sixth Form College, Cambridge](https://www.hillsroad.ac.uk). 

Fundamentally, the most important skill for any computer scientist is __problem-solving__, that is, how to formulate problems, consider solutions and to describe those solutions clearly and unambiguously in a programming language.  It's a skill that draws variously on Maths, Engineering, Science, Art and even philosophy - that's what make its fun!  It's not just about the code however, understanding how the computer works alongside the practical application of programming is important and this text endeavours to draw some lines between the theory and the practical.

The text is divided into twelve chapters, with a final thirteenth chapter bringing together many of the constructs and concepts learned.  The text could be covered during a first term of a programming class or worked through individually.  Each chapter introduces a number of topics based on an overarching theme.  Each new topic uses example programs to illustrate the new syntax and includes one or more practical programming tasks to complete during the sessions with extensions for self-study and homework.

Additionally, each chapter contains a section called __Extended Theory__.  Here we dig into some of the theoretical topics underpinning, where appropriate, the programming concepts from the chapter.  They may cover aspects of computer science that are unfamiliar but for students taking a course, e.g. A Level Computer Science, they provide useful supplementary material, explanation and, importantly, further example code.  These topics are indicated by a trailing asterisk in the left-hand menu.


This text deals exclusively with __console__ programming.  For many this will be an unusual environment as graphical user interfaces are increasingly the norm for our interactions with a computer.  This is sometimes known as __computation as calculation__ (a GUI would be __computation by interaction__) which has three steps:  INPUT, PROCESS, OUTPUT and the flow of control to the program is top-down as determined by the program logic.  With a GUI the flow of control is determined by when the user e.g. clicks a button, i.e. it captures __events__.

We deliberately do not cover the object-oriented paradigm, leaving that to a supplementary text.   Similarly, we stop short at advanced data structures. For experienced programmers this may seem an unusual decision particularly as C\# _is_ an object oriented language and using data structures i.e. stacks, graphs etc. make solving some problems considerably easier.  From the author's experience getting a solid foundation in the fundamental constructs of programming from an imperative/procedural context lays good foundations upon which to build for further development.  Thus, this text should be regarded very much as an introduction to the world of programming with C\#.

C\#,  was developed by Microsoft in 2000 as part of the .NET framework and some twenty years later it remains one of the most popular and widely used programming languages in the world.  In June 2019 it was 5th in the popularity rankings published by TIOBE, behind C, Java, Python and C++.  It can be used for web application development, Windows desktop applications and gaming.  It was developed by Microsoft for Windows so understandably you will need access to the Windows operating system to take advantage of all it can offer.  Microsoft has embraced the open-source movement of late so it is possible to develop on e.g. Linux systems.

## Requirements

To get started with the examples and exercises you will need access to an __Integrated Development Environment__, this is software that includes a text editor and a compiler to convert the code we write into an executable program.  One such tool is Visual Studio, the [Community edition](https://visualstudio.microsoft.com/vs/community/) is available as a free download for Windows.  Alternatively, Microsoft produce a more lightweight environment [Visual Studio Code](https://code.visualstudio.com/) which takes a bit more to set up and requires a C\# extension but is available for both Windows and Linux.  All source code in this text will run on either of these platforms.

!!! note
    Applications written in C\# use the .NET Framework.  There are plenty of web sites, including the [support documentation from Microsoft](https://docs.microsoft.com/en-us/visualstudio/install/install-visual-studio?view=vs-2019), that explain how to install either of these environments to get started with C\# so this will not be repeated here.

## Tips for success

1. From the moment you start through to when you finish any computer science course new technologies will have been developed, it is advisable therefore to keep as up to date as you can by reading blogs and articles about programming and C\# in particular.
2. Practice, practice, practice (and then do some more practice)!  Programming is like learning a musical instrument, it takes time, it takes a lot of practice
3. Develop good coding habits e.g.
  
   - Make your code self-documenting i.e. name all files and variables so they are descriptive
   - Format your code, make use of line breaks and indentation
   - Plan before you program
   - Keep the length of functions/subroutines to a "screen full"

4. Spend time with the IDE (Integrated Development Environment) you are using to write your programs, esp. the debugger
1. Document your code, keep a README.md file in your project explaining what the program does and how to get it up and running
2. Use Git (and GitHub) for repositories of your projects
3. Always think who else might read your code, does it make sense?
4. Never stop learning!
9. It's OK to ask for help
10. Did I mention practice ...?

## For information

- All code for this text was written using [Visual Studio Code](https://code.visualstudio.com/)
- The text itself was written in [Markdown](https://daringfireball.net/projects/markdown/), again using [Visual Studio Code](https://code.visualstudio.com/)
- A [print version](#) is available and was built using [Pandoc](https://pandoc.org/)
- This site was built using [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- The text and all code samples, plus sample answers to selected exercises are all available in a Git Hub repository: [https://github.com/sahumphreys/csharpprogramming.git](https://github.com/sahumphreys/csharpprogramming.git)

[^1]: If you have programmed before in Python Appendix 7 provides a summary of the differences in syntax between the two languages.
