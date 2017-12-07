Used to obtain the `System.Type` object for a type. A `typeof` expression takes the following form:

```C#
System.Type type = typeof(int); 
```

## Remarks
To obtain the run-time type of an expression, you can use the .NET Framework method `GetType`, as in the following example:

```C#
int i = 0;  
System.Type type = i.GetType(); 
```

The `typeof` operator cannot be overloaded. 

The `typeof` operator can also be used on open generic types. Types with more than one type parameter must have the appropriate number of commas in the specification. The following example shows how to determine whether the return type of a method is a generic IEnumerable<T>. Assume that method is an instance of a MethodInfo type:

```C#
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);
```

## Example 1

```C#
public class ExampleClass
{
   public int sampleMember;
   public void SampleMethod() {}

   static void Main()
   {
      Type t = typeof(ExampleClass);
      // Alternatively, you could use
      // ExampleClass obj = new ExampleClass();
      // Type t = obj.GetType();

      Console.WriteLine("Methods:");
      System.Reflection.MethodInfo[] methodInfo = t.GetMethods();

      foreach (System.Reflection.MethodInfo mInfo in methodInfo)
         Console.WriteLine(mInfo.ToString());

      Console.WriteLine("Members:");
      System.Reflection.MemberInfo[] memberInfo = t.GetMembers();

      foreach (System.Reflection.MemberInfo mInfo in memberInfo)
         Console.WriteLine(mInfo.ToString());
   }
}
/*
 Output:
    Methods:
    Void SampleMethod()
    System.String ToString()
    Boolean Equals(System.Object)
    Int32 GetHashCode()
    System.Type GetType()
    Members:
    Void SampleMethod()
    System.String ToString()
    Boolean Equals(System.Object)
    Int32 GetHashCode()
    System.Type GetType()
    Void .ctor()
    Int32 sampleMember
*/
```

## Example 2

This sample uses the `GetType` method to determine the type that is used to contain the result of a numeric calculation. This depends on the storage requirements of the resulting number.

```C#
class GetTypeTest
{
    static void Main()
    {
        int radius = 3;
        Console.WriteLine("Area = {0}", radius * radius * Math.PI);
        Console.WriteLine("The type is {0}",
                          (radius * radius * Math.PI).GetType()
        );
    }
}
/*
Output:
Area = 28.2743338823081
The type is System.Double
*/
```

## References
1. [typeof (C# Reference)](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/typeof)