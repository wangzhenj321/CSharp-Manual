## Question
I want to know about unmanaged resources. Can anyone please give me a basic idea?

## Answer

Managed resources basically mean "managed memory" that is managed by the garbage collector. When you no longer have any references to a managed object (which uses managed memory), the garbage collector will (eventually) release that memory for you.

Unmanaged resources are then everything that the garbage collector does not know about. For example:
- Open files
- Open network connections
- Unmanaged memory
- In XNA: vertex buffers, index buffers, textures, etc.

Normally you want to release those unmanaged resources before you lose all the references you have to the object managing them. You do this by calling `Dispose` on that object, or (in C#) using the using statement which will handle calling `Dispose` for you.

If you neglect to `Dispose` of your unmanaged resources correctly, the garbage collector will eventually handle it for you when the object containing that resource is garbage collected (this is "finalization"). But because the garbage collector doesn't know about the unmanaged resources, it can't tell how badly it needs to release them - so it's possible for your program to perform poorly or run out of resources entirely.

If you implement a class yourself that handles unmanaged resources, it is up to you to implement `Dispose` and `Finalize` correctly.

## References
1. [What exactly are unmanaged resources?](https://stackoverflow.com/questions/3433197/what-exactly-are-unmanaged-resources)