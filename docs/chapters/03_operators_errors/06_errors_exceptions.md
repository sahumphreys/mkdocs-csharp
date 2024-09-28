---
title: Errors and Exceptions
---

# {{ title }}

In programming, it is crucial to ensure that the program functions as intended and that the data being processed is accurate. Correct data is vital because organizations rely on it, data protection laws require it, and incorrect data can lead to unexpected behavior or crashes in the program.

## Types of Errors

There are several types of errors that can occur during programming:

- **Syntax Error**: The program does not adhere to the rules of the programming language. These errors prevent the program from compiling and are detected by the compiler during the build process.
  
- **Logic Error**: The code compiles successfully, and the program runs, but the output is incorrect. This type of error indicates a flaw in the algorithm or logic used in the program.
  
- **Runtime Error**: An error that occurs while the program is running, often causing the application (and sometimes the operating system) to crash. For example, entering a string when a numeric input is expected in a temperature conversion program can lead to a runtime error.

Each type of error is detected in different ways:

- **Syntax errors** are identified by the compiler, though the error messages it produces can be cryptic.
  
- **Logic errors** must be detected and corrected by the programmer through careful testing and debugging.
  
- **Runtime errors** require the programmer to anticipate potential issues and handle them appropriately.

## Validation of Data Entry

To minimize runtime and logic errors when users enter data, programmers can implement various checks:

- **Checking the Length of a String**: Input data may need to conform to a fixed length (e.g., bank account numbers). This can be easily validated using the `Length` property of the string.
  
- **Checking the Data Format**: Ensure the input meets specific format criteria, such as being all uppercase, lowercase, or following a specific pattern. Regular expressions are particularly useful for this purpose.
  
- **Checking the Range of Data**: For example, students in a school are usually 18 years old or younger. When a date of birth is entered, the range of acceptable dates can be validated.
  
- **Checking Required Fields**: Data entry forms often have fields that must be completed. If the user omits any required data, the program should alert them to provide it.
  
- **Checking Data Types**: This is best handled through **exception handling**.

## Exception Handling

!!! note "From the syllabus"
    AQA: Exception handling (3.1.1.9/4.1.1.9)}
    
    - Be familiar with the concept of exception handling; Know how to use exception handling in a programming language.

Most programming languages feature **Exception Handling** to manage potential runtime errors that could cause the program to crash during execution. Examples include:

- Attempting to convert a non-numeric string into an integer or floating-point number.
- Trying to read data from a non-existent file.
- Dividing by zero.
- Performing calculations with non-numeric data.

When a runtime error occurs, the system generates an **exception**. Programmers can include instructions in the code to define how the system should respond to such exceptions. It is usually possible to identify the type of exception, enabling different handling for various errors.

Consider the example program below, where a user can inadvertently crash the program by entering a non-numeric value (e.g., "sheep") for the radius of a circle. The program cannot convert "sheep" into a number, triggering an exception:

```cs
Console.WriteLine("Program to calculate the circumference of a circle");
Console.Write("Enter circle radius: ");
try
{
    double radius = Convert.ToDouble(Console.ReadLine());
    double diam = radius * 2;
    double circ = Math.PI * diam; // Use Math.PI for consistency
    Console.WriteLine("The circumference of the circle = " + circ.ToString());
}
catch (System.FormatException ex) // Use 'ex' as a common abbreviation
{
    Console.WriteLine(ex.Message);
    Console.WriteLine("Please enter a valid number.");
}
Console.ReadLine();
```

In this code:
- The `try { ... } catch { ... }` block first attempts to handle the user's input. If it encounters unexpected data, it catches the exception and handles it gracefully, preventing a crash.
- Using `Math.PI` is preferable to using a hardcoded value for π, ensuring greater accuracy.

While there is much more to exception handling (such as customizing actions based on the type of error), this overview provides a solid starting point for understanding its importance in robust programming.
