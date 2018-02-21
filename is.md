Checks if an object is compatible with a given type, or (starting with C# 7) tests an expression against a pattern.

## Testing for type compatibility

The `is` keyword evaluates type compatibility at runtime. It determines whether an object instance or the result of an expression can be converted to a specified type. It has the syntax
```c#
expr is type
```
where *expr* is an expression that evaluates to an instance of some type, and *type* is the name of the type to which the result of *expr* is to be converted. The `is` statement is `true` if *expr* is non-null and the object that results from evaluating the expression can be converted to *type*; otherwise, it returns `false`.

## Pattern matching with `is`

#### Type pattern

When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type. It is a straightforward extension of the `is` statement that enables concise type evaluation and conversion. The general form of the `is` type pattern is:
```c#
expr is type varname
``` 
where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.

#### Constant pattern

When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant. In C# 6 and earlier versions, the constant pattern is supported by the `switch` statement. Starting with C# 7, it is supported by the `is` statement as well. Its syntax is:
```c#
expr is constant
```
where *expr* is the expression to evaluate, and *constant* is the value to test for. *constant* can be any of the following constant expressions:
- A literal value.
- The name of a declared `const` variable.
- An enumeration constant.

## References

1. [is (C# Reference)](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/is)
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM5ODg0MzA5NV19
-->