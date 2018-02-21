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

- The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET Framework namespace `System` ([Namespaces (C# Programming Guide)](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/namespaces/)).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjAxODQxODMzMV19
-->