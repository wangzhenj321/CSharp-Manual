Well, neither keyword is present in the language, so the question is somewhat vague. The best that can be done is to look how each term is used in C# language specification (1.6.6.1 "Parameters"):

> Parameters are used to pass values or variable references to methods. The parameters of a method get their actual values from the arguments that are specified when the method is invoked.

So, "parameters" refer to names, and "arguments" refer to values bound to those names. E.g.:

```C#
void Foo(int x, int y); // x and y are parameters (形参)
Foo(1, 2);              // 1 and 2 are arguments (实参)
```

## References
1. [Difference between arguments/parameters in C#](https://stackoverflow.com/questions/1663705/difference-between-arguments-parameters-in-c-sharp)