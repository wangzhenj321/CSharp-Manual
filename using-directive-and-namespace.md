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
- To create an alias for a namespace or a type. This is called a using alias directive.
	```c#
	using Project = PC.MyCompany.Project; 
	```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjAyMTE3Njc5NF19
-->