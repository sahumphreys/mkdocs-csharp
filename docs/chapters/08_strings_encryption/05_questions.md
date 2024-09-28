---
title: Questions
---

# {{ title }}

1. A function `sqrt(x)` returns the square root of a positive integer `x`.  The following table shows three values used to test the functionality of this function.  State in each case the  __different__ type of test data being used in each case.

    | `x` | Type of test data |
    | ------- | ----------------- |
    |   49    |                   |
    |    -8   |                   |
    |    1    |                   |

2. Write a regular expression to match with a given credit card number which starts with either the digits $34$ or $37$ and is followed by 13 more digits

3. A regular expression for a valid identifier in a programming language can be described as `[A-Za-z][A-Za-z0-9_]*`.  State whether the following identifiers would be valid in this language

    a. Form1

    b. outer_loop

    c. \_unknown

    d. anon\_

4. Here is a regular expression: `^[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+$` For what input is this designed to test?

// MORE TO ADD

## Additional Exercises

1. Write a program that reads a string, reverses it and prints it to the screen. For example: "hello" -> "olleh".
2. Create a string checking program that will:
   - Store the string "I am going to check every word of this sentence for the keywords"
   - Split the string into an array of the individual words making up the sentence
   - Check the array of words for instances of these keywords: check, word, sentence
   - Output the sentence with the keywords highlighted in a different console colour (Use e.g. `Console.ForegroundColor = ConsoleColor.Red`)
3. Write a program that reads a string from the console and prints in alphabetical order all letters from the input string and how many times each one of them occurs in the string.
4. Write a program that extracts all the text without any tags and attribute values from an HTML document. (Hint: Scan the text letter by letter, keep in a variable whether there is an opening tag which has not been closed.  If you have a letter add it to the result only when the closing tag has been encountered.)
5. The rules for identifiers in a programming language can be defined as a regular expression patter: `"[A-Za-z][A-Za-z0-9_]*"`.  State whether the following are valid or invalid according to this pattern:
    - Form1
    - outer_loop
    - _myAge
    - myAge_
