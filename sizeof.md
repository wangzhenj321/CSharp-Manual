Used to obtain the size in bytes for an unmanaged type. Unmanaged types include the built-in types that are listed in the table that follows, and also the following:
- Enum types
- Pointer types
- User-defined structs that do not contain any fields or properties that are reference types

The following example shows how to retrieve the size of an `int`:

```C#
// Constant value 4:  
int intSize = sizeof(int); 
```

## Remarks
Starting with version 2.0 of C#, applying `sizeof` to built-in types no longer requires that unsafe mode be used.

The `sizeof` operator cannot be overloaded. The values returned by the `sizeof` operator are of type `int`. The following table shows the constant values that are substituted for `sizeof` expressions that have certain built-in types as operands.

|**Expression**|**Constant value**|
|--------------|------------------|
|sizeof(sbyte) |1|
|sizeof(byte)  |1|
|sizeof(short) |2|
|sizeof(ushort)|2|
|sizeof(int)   |4|
|sizeof(uint)  |4|
|sizeof(long)  |8|
|sizeof(ulong) |8|
|sizeof(char)  |2 (Unicode)|
|sizeof(float) |4|
|sizeof(double)|8|
|sizeof(decimal) |16|
|sizeof(bool)  |1|

For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks. Although you can use the Marshal.SizeOf method, the value returned by this method is not always the same as the value returned by `sizeof`. Marshal.SizeOf returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.

## References
1. [sizeof (C# Reference)](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/sizeof)