When the C# compiler encounters an #if directive, followed eventually by an #endif directive, it will compile the code between the directives only if the specified symbol is defined. Unlike C and C++, you cannot assign a numeric value to a symbol; ***the #if statement in C# is Boolean and only tests whether the symbol has been defined or not***. For example,

```C#
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif
```

You can use the operators == (equality), != (inequality) only to test for true or false . True means the symbol is defined. The statement #if DEBUG has the same meaning as #if (DEBUG == true). You can use the operators && (and), || (or), and ! (not) to evaluate whether multiple symbols have been defined. You can also group symbols and operators with parentheses.

## Remarks

#if, along with the #else, #elif, #endif, #define, and #undef directives, lets you include or exclude code based on the existence of one or more symbols. This can be useful when compiling code for a debug build or when compiling for a specific configuration.

A conditional directive beginning with a #if directive must explicitly be terminated with a #endif directive.

#define lets you define a symbol, such that, by using the symbol as the expression passed to the #if directive, the expression will evaluate to true.

You can also define a symbol with the /define compiler option. You can undefine a symbol with #undef.

***A symbol that you define with /define or with #define does not conflict with a variable of the same name. That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.***

The scope of a symbol created with #define is the file in which it was defined.

## Example

```C#
// preprocessor_if.cs  
#define DEBUG
#define MYTEST  
using System;  
public class MyClass   
{  
    static void Main()   
    {  
#if (DEBUG && !MYTEST)  
        Console.WriteLine("DEBUG is defined");  
#elif (!DEBUG && MYTEST)  
        Console.WriteLine("MYTEST is defined");  
#elif (DEBUG && MYTEST)  
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else  
        Console.WriteLine("DEBUG and MYTEST are not defined");  
#endif  
    }  
}
```

## References
1.[#if (C# Reference)](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if)
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTgwNjgzNDQyMywxMjk3NDQ0MDYzXX0=
-->