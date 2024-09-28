---
title: Switch
---

# {{ title }}

The `switch` statement is a powerful control structure in C# that simplifies complex conditional logic, making code easier to read and maintain. We previously saw the `switch` statement in the cards program from an earlier chapter.

## Advantages of Using Switch

Nested `if` statements can become difficult to read and manage. The `switch` construct offers a cleaner and more straightforward alternative for making multi-way decisions.

### Example: Grades Program

Here’s an example illustrating the use of the `switch` statement in a grading system. The value of the variable `grade` determines which message is displayed on the screen.

```csharp
static void Main(string[] args) {
    char grade = 'B';
    
    switch (grade) {
        case 'A':
            Console.WriteLine("Excellent!");
            break;
        case 'B':
        case 'C':
            Console.WriteLine("Well done!");
            break;
        case 'D':
            Console.WriteLine("You passed.");
            break;
        case 'F':
            Console.WriteLine("Better try again.");
            break;
        default:
            Console.WriteLine("Invalid grade.");
            break;
    }
    
    Console.WriteLine($"Your grade is {grade}.");
}
```

### Key Features of Switch

- **Conciseness**: The `switch` statement is generally more concise than a series of `if-else` statements, enhancing code readability.
- **Break Statement**: The use of `break` after each `case` is crucial. It exits the switch block once the matched case executes, preventing the fall-through behavior where subsequent cases would execute unintentionally. This is illustrated with cases `B` and `C`, which share the same output.
- **Default Case**: If none of the specified cases match the `grade`, the `default` case executes, providing a fallback for invalid inputs.

### Valid Selector Types

The `switch` construct can be utilized with a selector of type:
- **Integer**
- **Character (`char`)**
- **String**
- **Enum** (which will be introduced later)

Using a `switch` statement effectively can streamline your decision-making processes in programming, making your code not only shorter but also clearer and easier to follow.
