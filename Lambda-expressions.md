A lambda expression is an unnamed method written in place of a delegate instance. The compiler immediately converts the lambda expression to either:
- A delegate instance
- An expression tree

Given the following delegate type:

```C#
delegate int Transformer (int i);
```

we could assign and invoke the lambda expression `x => x * x` as follows:

```C#
Transformer sqr = x => x * x;
Console.WriteLine(sqr(3));    // 9
```

> Internally, the compiler resolves lambda expressions of this type by writing a private method, and moving the expression's code into that method.

## Explicitly specifying lambda parameter types

```C#
Bar((int x) => Foo(x));
```

## Capturing outer variables

```C#
int factor = 2;
Func<int, int> multiplier = n => n * factor;
factor = 10;
Console.WriteLine(multiplier(3));    // 30
```

#### Capturing iteration variables

```C#
Action[] actions = new Action[3];

for (int i = 0; i < 3; i++)
    actions[i] = () => Console.Write(i);

foreach (Action a in actions) a();    // 333
```