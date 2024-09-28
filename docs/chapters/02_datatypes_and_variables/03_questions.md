---
title: Questions
---

# {{ title }}

Study the following program and answer the questions below:

```cs
using System;

namespace circle
{
    class circle
    {
        /* Program to calculate the circumference of a circle when the radius is known.
        NB. This program will not compile - you need to correct the errors */
        static void Main(string[] args)
        {
            const double PI = 3.14159;  // Corrected value of PI
            int radius;
            double diam;
            double circ; // Corrected type for circumference
            
            Console.WriteLine("Program to calculate the circumference of a circle");
            Console.Write("Enter circle radius: ");
            radius = Convert.ToInt32(Console.ReadLine()); // Added conversion
            diam = radius + 2;
            diam = PI * diam; // Added missing semicolon
            circ = diam; // Assigning value to circ
            Console.WriteLine("The circumference of the circle = " + circ.ToString()); // Corrected output line
            Console.ReadLine(); // Added closing parenthesis
        }
    }
}
```

1. The program contains a number of **syntax errors**. Can you spot them? 
2. The program contains a number of **logic errors**. Can you spot them?
3. What **runtime errors** might occur?
4. Explain how the program outputs to the console window, specifically mentioning the methods used.
5. Explain how user input is processed and converted into the correct data type.
6. Why might the input(s) need to be converted into another type of data?
7. Modify the program to output the area of the circle, as well as the circumference.
8. A teacher is planning to write a program to store test marks for their pupils. What data types should be chosen for the following values?
    - Surname of the student
    - Raw score for the test
    - Percentage mark for the test
    - Final grade awarded
    - Whether the student has passed or failed the test

## Programming Task: Temperature Conversion

1. Write a program that converts a temperature in degrees Fahrenheit into Celsius. 

    !!! tip
           What variables will you need? What should you call them, and what type should they be? How can you test the program? What runtime errors might occur?

2. Extend the program to reverse the operation, i.e., convert Celsius into Fahrenheit.

3. What is the value of the **integer** variable `answer` after executing each of the following statements (% is the modulus operator)?
    a. `answer = 35 / 7`;  
    b. `answer = 17 / 2`;  
    c. `answer = 17 % 2`;  

4. How would the value stored in `answer` differ if it was of type `double`?
    a. `answer = 35 / 7`;  
    b. `answer = 17 / 2`;  
    c. `answer = 17 % 2`;  

5. Look up the following terms: "Syntax error," "Logic error," and "Runtime error." Given the statement `CelTemp = (FahrTemp - 32) * 5 / 9;`, make changes to the statement to generate each of the three different types of error:

| Type of error | Modified statement | Effect of error |
| ------------- | ------------------ | --------------- |
| Syntax error  |                    |                 |
| Logic error   |                    |                 |  
| Runtime error  |                    |                 |

## Additional Exercises

1. What data types would be most appropriate for the following values:  
   a. 52   
   b. -115   
   c. 97   
   d. 12.345   
   e. 8923.123456   
   f. 3456.091124875956542151256683467

2. Write a program that compares two real numbers accurately to at least 0.000001.

3. Declare two variables of type `int`. Assign them the values 8 and 5. Swap their values and print them to the screen.

4. A college system wants to keep track of their students. Each student record will have both first name and last name recorded, their age, their gender, and a unique student number in the range 20210000 through to 20219999. Declare appropriate variables to hold this data.

5. Write a program that inputs the length and width of a rectangular garden. Calculate the area of the garden and the cost of turfing a lawn if a 1m un-turfed border is around the perimeter of the garden. Assume the cost of turf is 10 currency units per square meter.
