**Virtual methods have an implementation and provide the derived classes with the option of overriding it.**

**Abstract methods do not provide an implementation and force the derived classes to override the method.**

So, abstract methods have no actual code in them, and subclasses HAVE TO override the method. Virtual methods can have codes, which is usually a default implementation of something, and any subclasses CAN override the method using the override modifier and provide a custom implementation.

```C#
public abstract class E
{
    public abstract void AbstractMethod(int i);

    public virtual void VirtualMethod(int i)
    {
        // Default implementation which can be overridden by subclasses.
    }
}

public class D : E
{
    public override void AbstractMethod(int i)
    {
        // You HAVE to override this method
    }
    public override void VirtualMethod(int i)
    {
        // You are allowed to override this method.
    }
}
```

## References
1. [Difference between virtual and abstract methods](https://stackoverflow.com/questions/14728761/difference-between-virtual-and-abstract-methods)