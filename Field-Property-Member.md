#### Field

These are variables declared at the class level.

```C#
public class SomeClass
{
  private int someInteger; // This is a field
  public double someDouble; // This is another field
  protected StringBuidler stringBuidler; // Still another field
}
```

#### Property

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

#### Member

Includes fields, properties, methods, events of a class.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI0Njc1MTQxMF19
-->