---
title: What does it mean to program?
---

# {{ title }}

!!! note "In this chapter"
    - What does it mean to program?
    - Compiling **source code** into **object (machine) code**
    - Software development process
    - Use Visual Studio to build a first program
    - Getting data from the keyboard and printing to the screen

To **program** means to create sequences of instructions in a programming language that organize the work of the computer to carry out a specific task. The sequence of steps required to achieve this task is called an __algorithm__. An algorithm is then expressed in a __programming language__, or __code__, which is subsequently converted into __machine code__ for execution by the computer.

C\# is a __high-level language__. High-level languages enable the programmer to focus on the problem being solved without worrying about the specific architecture of the machine. The syntax of high-level languages is closer to English, making them easier to read, write, and maintain.

By contrast, a __low-level language__ is much closer to the machine code of the target computer. Machine code is written using binary (1s and 0s) and is specific to a particular CPU architecture. 

High-level languages need to be either __compiled__ or __interpreted__ into machine code for a specific CPU platform. A __compiler__ converts the source code into a separate, stand-alone, executable file that can be distributed and executed. The compiler checks if the instructions are syntactically and semantically correct before converting them into machine code. This process includes verifying correct punctuation, keyword usage, and logical consistency of the instructions.

!!! note "From the syllabus"
    **AQA**: Understand the role of a compiler; understand the difference between **source code** and **object (executable) code** (3.6.3.1/4.6.3.1).
    
    - A **compiler** takes the source code written in a high-level programming language and converts it into executable code (the machine code that can be run by a processor). It translates a program from a human-readable format to a machine-readable format.

## Stages in Software Development

Writing software can be complex and time-consuming. In the professional world, software is usually developed by teams and goes through several stages. When learning to program, you may not work in a team, but it's still important to follow these stages as you build your solutions:

1. **Gather the Requirements**: 
      - What is the software supposed to do? What will the user be required to do when they interact with your software? This usually includes a list of measurable objectives. Before a problem can be solved, it has to be clearly defined with the objectives of the solution determined, often with input from the intended users.

2. **Planning**:
      - What type of application is being developed (e.g., console, desktop, web app, mobile, etc.)? What data will the program need to handle, and what are their types and structures? What are the algorithms that will operate on this data? What inputs and outputs will the program need? Time spent thinking through the organization of your application will save a lot of effort when it comes to programming, debugging, and maintaining the solution.

3. **Implementation**:
      - At this stage, the source code is written according to the objectives from stage 1 and the design from stage 2. This is usually an iterative process, often involving prototyping to refine the solution.

4. **Testing**:
      - Have all the requirements been met? Does the program work as intended? Testing should be carried out with well-chosen test data, covering normal, boundary, and erroneous cases to ensure the program behaves correctly in all situations.

5. **Deployment**:
      - This stage involves releasing the software for use by others. While not usually relevant for small learning projects, in professional settings, deployment is a crucial phase where the software is made available to users.

6. **Documentation**:
      - This is not a separate stage but should be integrated throughout the process. Keeping good documentation habits—recording what you are doing, what has worked, what went wrong, and what tests you have run—is invaluable for maintaining and updating your software.

!!! note "From the syllabus"
    **AQA**: Systematic approach to problem solving (4.13.1).
    
    - There are several approaches to developing software, including Agile and Waterfall, but all processes include stages like **Analysis**, **Design**, **Implementation**, **Testing**, and **Evaluation**.
    - The timing and manner of these stages may vary depending on the process, but they will always be present.
    - Use even small programming tasks to practice each of these stages.

Thus, programming is much more than just writing code; it is part of a larger process. Always remember, we write code to be used, often by others. As beginners, we take on the roles of both the designer/programmer and the user. It's important to get used to separating these roles when designing and executing your programs.
