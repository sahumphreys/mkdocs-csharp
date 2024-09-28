---
title: Declaring, Implementing, and Invoking a Method
---

# {{ title }}

There are three main stages involved in working with methods in C#:

1. **Declaration**
2. **Implementation**
3. **Invocation**

Let's go through each stage step-by-step, using examples to illustrate the concepts.

## Declaration of a Method

When you declare a method, you define its name, return type, and any parameters it takes. Let’s revisit the `Caesar Cipher` program, starting with the automatically generated code in Visual Studio when you created the project:

```cs
namespace CaesarCipher
{
    class CaesarCipher
    {
        static void Main(string[] args)
        {
            // code body
        }
    }
}
```

In this code, Visual Studio generated a class named `CaesarCipher` with a method named `Main()`. Notice the curly braces `{ ... }` enclosing the body of both the class and the method.

- The `class` keyword declares the `CaesarCipher` class.
- The `Main()` method is the entry point of the program and is declared inside the `CaesarCipher` class.

We can add more methods to this class. For example:

```csharp
namespace CaesarCipher
{
    class CaesarCipher
    {
        static void Main(string[] args)
        {
            // Calling other methods from Main()
            DisplayGreeting();
            EncryptMessage();
        }

        static void DisplayGreeting()
        {
            Console.WriteLine("Welcome to the Caesar Cipher Program!");
        }

        static void EncryptMessage()
        {
            // code to encrypt a message
        }
    }
}
```

Here, two additional methods (`DisplayGreeting()` and `EncryptMessage()`) have been declared within the `CaesarCipher` class.

### Components of a Method Declaration

Every method declaration includes the following elements, in this order:

1. **Return Type**: Specifies what kind of data the method will return. If the method doesn't return any value, the return type is `void`.
2. **Method Name**: A descriptive name that starts with an uppercase letter and follows PascalCase naming convention.
3. **Parameter List**: A comma-separated list of parameters enclosed in parentheses. Parameters provide input values to the method and can be empty.

Let’s analyze the `Main()` method again:

```csharp
static void Main(string[] args)
{
    // method body
}
```

- **Return Type**: `void` means this method doesn't return any value, making it a _procedure_. If it returned a value, we would use types like `int` or `string`, making it a _function_.
- **Method Name**: `Main` is the default entry point of a C# program, and it must be named exactly `Main`.
- **Parameter List**: `(string[] args)` is an array of strings named `args`. This allows the program to accept command-line arguments when it starts.

#### Access Modifiers

Methods can also have access modifiers that control their visibility:

- **`public`**: The method can be accessed from outside the class.
- **`private`**: The method can only be accessed from within the same class (default if no access modifier is specified).
- **`protected`**: The method can only be accessed within its class and by derived classes.

The `static` keyword means the method belongs to the class itself, not to an instance of the class. This concept is fundamental in object-oriented programming (OOP) and can be explored further as you progress.

### Method Naming Conventions

- Start with an uppercase letter.
- Use PascalCase (e.g., `CalculateSum()`).
- Prefer descriptive names, ideally a verb or verb-noun combination (e.g., `PrintReport()`).
- Avoid abbreviations and keep the name meaningful.

## Implementation of a Method

Implementing a method means writing the code that performs the task described by the method name. The code is placed between the curly braces following the method declaration. For example:

```csharp
static void ExitConsole()
{
    Console.WriteLine("Press any key to continue...");
    Console.ReadKey();
}
```

This method displays a message and waits for the user to press a key before exiting.

### Local Variables

Variables declared inside a method are called _local variables_ because their scope is limited to the method. Once the method finishes executing, these variables are no longer accessible.

```csharp
static int GetInt()
{
    Console.Write("Enter an integer: ");
    int number = Convert.ToInt32(Console.ReadLine());
    return number;
}
```

In this example, `number` is a local variable. It only exists within the `GetInt()` method and is not accessible outside.

### Scope of Local Variables

Local variables are only in scope within the code block they are declared in. For example, variables declared in a `for` loop only exist while the loop is executing.

```csharp
for (int i = 0; i < 5; i++)
{
    int temp = i * 2;  // temp is only accessible inside the loop
}
```

## Invoking or Calling a Method

**Invoking** or **calling** a method is done by writing its name followed by parentheses. If the method requires parameters, you provide them inside the parentheses.

```csharp
int x = GetInt();  // GetInt() is called and its return value is stored in x
ExitConsole();     // ExitConsole() is called but does not return a value
```

- `GetInt()` returns an integer, so its return value is stored in the variable `x`.
- `ExitConsole()` doesn’t return a value, so it can be called on its own line.

### Passing Parameters to Methods

Methods can take parameters that are passed in when the method is called. For example:

```csharp
static void PrintMessage(string message)
{
    Console.WriteLine(message);
}

PrintMessage("Hello, world!");
```

The `PrintMessage()` method accepts a string parameter `message` and prints it to the console.

## Summary

Understanding the stages of method declaration, implementation, and invocation is crucial for structuring programs effectively in C#. Practice by creating different methods, experimenting with return types and parameters, and calling them from the `Main()` method.
