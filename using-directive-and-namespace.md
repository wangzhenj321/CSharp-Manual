## using directive

The `using` directive has three uses:

- To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:
	```c#
	using System.Text; 
	```
- To allow you to access static members of a type without having to qualify the access with the type name.
	```c#
	using static System.Math;
	```
- To create an alias for a namespace or a type. This is called a *using alias directive*.
	```c#
	using Project = PC.MyCompany.Project; 
	```
The `using` keyword is also used to create *using statements*, which help ensure that IDisposable objects such as files and fonts are handled correctly.

**Reference** : [using Directive (C# Reference)](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/using-directive)

## namespace

### `global`

- The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET Framework namespace `System` ([Namespaces (C# Programming Guide)](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/namespaces/)). To be exactly, the `global::System` is not always to refer to the .NET Framework namespace `System`, sometimes it also refers to the user-defined namespace `System`.
	```c#
	namespace System
    {
        public class Console
        {
        }
    }
	```

- Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace. This unnamed namespace, sometimes referred to as the global namespace, is present in every file. Any identifier in the global namespace is available for use in a named namespace ([namespace (C# Reference)](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/namespace)).

### `::`

Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types. For example, consider this example:
```c#
using Alias = System;
```
```c#
namespace Library
{
    public class C : Alias.Exception { }
}
```
This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead. Using `Alias::Exception` insures that `Alias` is treated as a namespace alias and not mistaken for a type.

### Refe
<!--stackedit_data:
eyJoaXN0b3J5IjpbODU1OTYxNjE3XX0=
-->