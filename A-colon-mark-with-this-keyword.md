## Question
Before the `this` keyword is a colon. Can anyone explain what the colon means in this context? I don't believe this is inheritance.

```C#
using System;

namespace LinkedListLibrary
{
    class ListNode
    {
        private object data;
        private ListNode next;

        public ListNode(object dataValue) : this(dataValue, null) {}

        public ListNode(object dataValue, ListNode nextNode)
        {
            data = dataValue;
            next = nextNode;
        }

        public ListNode Next
        {
            get { return next; }
            set { next = value; }
        }
        public object Data
        {
            get { return data; }
        }
    }
}
```

## Answer
It (along with the `this` keyword) is instructing the constructor to call another constructor within the same type before it, itself executes.

Therefore:

```C#
public ListNode(object dataValue) : this(dataValue, null) {}
```

effectively becomes:

```C#
public ListNode(object dataValue)
{
    data = dataValue;
    next = null;
}
```

Note that you can use `base` instead of `this` to instruct the constructor to call a constructor in the base class.

## References
1. [What does this colon (:) mean?](https://stackoverflow.com/questions/1071148/what-does-this-colon-mean)