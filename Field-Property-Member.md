### Field

These are variables declared at the class level.

```C#
public class SomeClass
{
  private int someInteger; // This is a field
  public double someDouble; // This is another field
  protected StringBuidler stringBuidler; // Still another field
}
```

### Property

Often used as accessors to a private field of a class, they can provide get and set methods that wrap some logic around the field manipulation.

```C#
public class SomeClass
{
  private StringBuilder stringBuilder;

  // Property declaration
  public StringBuilder StringBuilder
  {
    get 
    { 
      if(this.stringBuilder == null)
        this.stringBuilder = new StringBuidler();

      return this.stringBuilder;
    }
    set
    {
      if(this.stringBuilder == null)
        this.stringbuilder = value;
    }
  }
}
```

#### Property vs Field

Properties expose fields. Fields should (almost always) be kept private to a class and accessed via get and set properties. Properties provide a level of abstraction allowing you to change the fields while not affecting the external way they are accessed by the things that use your class.

```c#
public class MyClass
{
    // this is a field.  It is private to your class and stores the actual data.
    private string _myField;

    // this is a property. When accessed it uses the underlying field,
    // but only exposes the contract, which will not be affected by the underlying field
    public string MyProperty
    {
        get
        {
            return _myField;
        }
        set
        {
            _myField = value;
        }
    }

    // This is an AutoProperty (C# 3.0 and higher) - which is a shorthand syntax
    // used to generate a private field for you
    public int AnotherProperty{get;set;} 
}
```

@Kent points out that Properties are not required to encapsulate fields, they could do a calculation on other fields, or serve other purposes.

@GSS points out that you can also do other logic, such as validation, when a property is accessed, another useful feature.

### Member

Includes fields, properties, methods, events of a class.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTk1MDQ4Njc1NV19
-->