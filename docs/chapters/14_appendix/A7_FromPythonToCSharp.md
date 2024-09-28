---
title: Appendix 7 - From Python to C#
---

If you've done any programming before, it's likely you've used Python, as its popularity in schools as a first programming language has grown significantly in recent years. This section summarizes some of the key differences between Python and C# by comparing simple code snippets and highlighting key concepts.

## Basic Syntax Comparison

**Python Example**

```python
# Python
userName = input("Enter your name > ")
print("Your name is ", userName)
```

**C# Example**

```csharp
using System;
namespace printName
{
    public class PrintName
    {
        static void Main(string[] args)
        {
            string userName;
            userName = Console.ReadLine();
            Console.WriteLine("Your name is " + userName);
        }
    }
}
```

### Key Differences

- Every C# program **must** define a class, and code is written inside that class.
- Every variable and method must be assigned a data type.
- The entry point for a C# program must be a method named `Main()`.

The Python code can be structured similarly to C#:

```python
def main():
    userName = input("Enter your name > ")
    print("Your name is ", userName)

if __name__ == '__main__':
    main()
```

Notice in C#:

- Every project will be in a `namespace` to organize code.
- Curly braces `{ ... }` define code blocks, unlike Python’s indentation.
- Each statement ends with a semi-colon, `;`.

## Data Typing

Python is dynamically typed, meaning variable types are determined at runtime and can change during the program. C# is statically typed, meaning variable types are set before compilation and cannot change. 

**Example**

```python
# Python
myVar = 5
myVar = "Hello"  # Now myVar is a string
```

```csharp
// C#
int myVar = 5;
// myVar = "Hello"; // Error: cannot assign a string to an int
```

In C#, you must declare variable types explicitly, and they cannot change type.

## Comments

- **Single-line comments**: Use `//`
- **Multi-line comments**: Use `/* ... */`

```csharp
// This is a single-line comment
/* 
 * This is a multi-line comment 
 * spanning multiple lines
 */
```

## Flow of Control

- C# uses curly braces `{ ... }` for code blocks instead of indentation.
- Conditions must be enclosed in parentheses `(...)`.
- Use `else if` instead of `elif`.
- C# includes a `switch` statement for multi-way branching.

**Example**

| Python                | C#                                        |
|-----------------------|-------------------------------------------|
| `if x > 0:`           | `if (x > 0) { ... }`                      |
| `elif x == 0:`        | `else if (x == 0) { ... }`                |
| `for i in range(5):`  | `for (int i = 0; i < 5; i++) { ... }`     |
| `for item in list:`   | `foreach (var item in list) { ... }`      |

## Boolean Expressions

- **C# uses `true` and `false` instead of `True` and `False`.**
- Boolean operators:
  - `and` -> `&&`
  - `or` -> `||`
  - `not` -> `!`

## Data Structures

- C# arrays have fixed sizes, whereas `List` is used for dynamic sizes.
- Lists in C# must specify the data type:

```csharp
List<int> numbers = new List<int>();
numbers.Add(5);
```

## Classes

C# supports creating user-defined classes with their own properties and methods. It also supports inheritance and access modifiers.

**Python**

```python
class MyClass(BaseClass):
    def __init__(self, x):
        self.x = x

MyObject = MyClass(42)
```

**C#**

```csharp
class MyClass : BaseClass
{
    public MyClass(int x)
    {
        this.x = x;
    }
}
MyClass MyObject = new MyClass(42);
```

### Access Modifiers

| Modifier   | Visibility                          |
|------------|-------------------------------------|
| `public`   | Accessible from anywhere            |
| `internal` | Accessible only within the project  |
| `protected`| Accessible within class and subclasses |
| `private`  | Accessible only within the class    |

## Memory Management

C# uses garbage collection for automatic memory management. However, for non-memory resources like files or network connections, you should manually release them using the `Dispose` pattern or the `using` statement.

```csharp
using (StreamWriter writer = new StreamWriter("file.txt"))
{
    writer.WriteLine("Hello, World!");
}
```

In Python, this is similar to using the `with` statement.

```python
with open('file.txt', 'w') as writer:
    writer.write("Hello, World!")
```

## Summary

Both Python and C# have their strengths and weaknesses. Understanding the differences in syntax, data types, and control structures will help you transition smoothly between these two languages.
