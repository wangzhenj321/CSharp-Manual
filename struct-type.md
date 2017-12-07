## Remarks

1. It is an error to define a default (parameterless) constructor for a struct.

2. Within a struct declaration, fields cannot be initialized unless they are declared as const or static.

3. Structs are value types and classes are reference types.

4. When writing a constructor with parameters for a struct, you must explicitly initialize all members; otherwise one or more members remain unassigned and the struct cannot be used, producing compiler error CS0171.

5. There is no inheritance for structs as there is for classes. A struct cannot inherit from another struct or class, and it cannot be the base of a class. Structs, however, inherit from the base class Object. A struct can implement interfaces, and it does that exactly as classes do.

6. Unlike classes, structs can be instantiated without using the new operator. In such a case, there is no constructor call, which makes the allocation more efficient. However, the fields will remain unassigned and the object cannot be used until all of the fields are initialized.

7. A struct can be used as a nullable type and can be assigned a null value.

## Example

```C#
public struct CoOrds
{
    public int x, y;

    public CoOrds(int p1, int p2)
    {
        x = p1;
        y = p2;
    }
}
```

```C#
// Declare a struct object without "new."
class TestCoOrdsNoNew
{
    static void Main()
    {
        // Declare an object:
        CoOrds coords1;

        // Initialize:
        coords1.x = 10;
        coords1.y = 20;

        // Display results:
        Console.Write("CoOrds 1: ");
        Console.WriteLine("x = {0}, y = {1}", coords1.x, coords1.y);

        // Keep the console window open in debug mode.
        Console.WriteLine("Press any key to exit.");
        Console.ReadKey();
    }
}
// Output: CoOrds 1: x = 10, y = 20
```

## References

1. [Structs](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/structs)

2. [Using Structs](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/using-structs)