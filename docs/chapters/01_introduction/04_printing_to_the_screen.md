---
title: Printing to the screen
---

# {{ title }}

!!! note "From the syllabus"
    Understand the differences between string concatenation, composite formatting, and string interpolation. Practice each method to become comfortable with displaying variables in formatted output.

There are multiple ways to display content on the screen in C#. Let's explore some of the most commonly used methods:

```cs
string name = "Mark";
var date = DateTime.Now;

// String concatenation:
Console.WriteLine("Hello " + name);
// Using composite formatting:
Console.WriteLine("Hello, {0}! Today is {1}, it's {2:HH:mm} now.", name, date.DayOfWeek, date);
// Using string interpolation:
Console.WriteLine($"Hello, {name}! Today is {date.DayOfWeek}, it's {date:HH:mm} now.");
```

In this example, we demonstrate three different techniques to print text to the console. Let’s break down each approach:

## Understanding the Code

1. **Comments**:  
   Lines beginning with `//` are comments. These lines are ignored by the compiler and serve to explain what the code is doing. Comments are invaluable for anyone reading your code, including your future self! Use comments to clarify complex logic or to note significant code sections. For multi-line comments, use the `/* ... */` syntax.

2. **String Concatenation**:  
   ```cs
   Console.WriteLine("Hello " + name);
   ```
   This method combines, or "concatenates," multiple strings together using the `+` operator. In this example, the string `"Hello "` is joined with the value of the `name` variable. It’s a straightforward technique but can become cumbersome when dealing with multiple variables.

3. **Composite Formatting**:  
   ```cs
   Console.WriteLine("Hello, {0}! Today is {1}, it's {2:HH:mm} now.", name, date.DayOfWeek, date);
   ```
   Here, numeric placeholders `{0}`, `{1}`, and `{2:HH:mm}` are used inside the string. They are replaced by the variables `name`, `date.DayOfWeek`, and `date` respectively, provided in the same order after the comma. This method allows for clear formatting but requires careful ordering of variables.

4. **String Interpolation**:  
   ```cs
   Console.WriteLine($"Hello, {name}! Today is {date.DayOfWeek}, it's {date:HH:mm} now.");
   ```
   This is the most modern and flexible way to format strings in C#. The `$` symbol before the string allows variables to be directly embedded inside curly braces `{ }`. This technique makes the code more readable and less error-prone.

1. **Using DateTime**:  
   In the example above, `DateTime.Now` retrieves the current date and time, storing it in the `date` variable. This allows us to display the current day and time dynamically.

## Task: Experimenting with Print Methods

__Modify the code to include additional information such as the user's age and the current year.__

1. Declare two new variables, `age` and `currentYear`, and assign appropriate values:

    ```cs
    int age = 25;
    var currentYear = DateTime.Now.Year;
    ```

2. Use all three print methods to display a message including the user’s name, age, and the current year. Add these lines to your code:

    ```cs
    // String concatenation
    Console.WriteLine("Hello " + name + ", you are " + age + " years old.");
    
    // Composite formatting
    Console.WriteLine("Hello, {0}! You are {1} years old. The year is {2}.", name, age, currentYear);
    
    // String interpolation
    Console.WriteLine($"Hello, {name}! You are {age} years old. The year is {currentYear}.");
    ```

1. Run the code to observe how each method outputs the message.

### Explanation of New Code

- The variable `age` is declared as an `int` (integer) and assigned a value of 25.
- `currentYear` is assigned the current year using `DateTime.Now.Year`.
- Each print statement includes both the name and age variables, and each uses a different formatting method.

### Conclusion

You’ve now explored three methods for printing to the console in C#. Each method has its use case and can be chosen based on the complexity and readability of the code you’re working with.

