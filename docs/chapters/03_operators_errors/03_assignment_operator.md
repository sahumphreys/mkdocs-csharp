---
title: Assignment operator
---

As noted this is the `=` operator.  Be careful with the difference between assignment and equality:

```cs
int a = 10;     // setting an initialiser (using =)
int b = a;      // a and b are equal (using =)
if (a == b)     // testing for equality using ==
{
    //
}         
```

The same variable can be assigned a different value during the program, the old value being lost when the new value is assigned.  When the variable is declared it can be given a start value, an __initialiser__.  Compound initialisation is permitted:

```cs
    int a, b, c;
    a = b = c = 10;
```

An assignment statement evaluates the right-hand size of the expression first producing a value, before assigning (copying) that value to the variable.  If we try to read the value of the variable before it has been assigned the default value for that variable, according to its data type, will be returned (see table in Chapter 2).

Some more syntactic sugar is __abbreviated assignment__ e.g.

```cs
    int a = 12;
    a += 2;         // same as a = a + 2, a is now 12
    a *= 3;         // same as a = a * 3, a is now 36
    a /= 3;         // same as a = a /3, a is now 4
```
