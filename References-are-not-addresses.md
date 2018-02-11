[NOTE: Based on some insightful comments I have updated this article to describe more clearly the relationships between references, pointers and addresses. Thanks to those who commented.]

I review a fair number of C# books; in all of them of course the author attempts to explain the difference between reference types and value types. Unfortunately, most of them do so by saying something like "*a variable of reference type **stores the address** of the object*". I always object to this. The last time this happened the author asked me for a more detailed explanation of why I always object, which I shall share with you now:

We have the abstract concept of "a reference". If I were to write about "Beethoven's Ninth Symphony", those two-dozen characters are not a 90-minute long symphonic masterwork with a large choral section. They're a reference to that thing, not the thing itself. And this reference itself contains references -- the word "Beethoven" is not a long-dead famously deaf Romantic Period composer, but it is a reference to one.

Similarly in programming languages we have the concept of "a reference" distinct from "the referent".

The inventor of the C programming language, oddly enough, chose to not have the concept of references at all. Rather, Ritchie chose to have "pointers" be first-class entities in the language. A pointer in C is like a reference in that it refers to some data by tracking its location, but there are more smarts in a pointer; you can perform arithmetic on a pointer as if it were a number, you can take the difference between two pointers that are both in the interior of the same array and get a sensible result, and so on.

Pointers are strictly "more powerful" than references; **anything you can do with references you can do with pointers**, but not vice versa. I imagine that's why there are no references in C -- it's a deliberately austere and powerful language.

The down side of pointers-instead-of-references is that pointers are hard for many novices to understand, and make it very very very easy to shoot yourself in the foot.

Pointers are typically implemented as **addresses**. An address is a number which is an offset into the "array of bytes" that is the entire virtual address space of the process (or, sometimes, an offset into some well-known portion of that address space -- I'm thinking of "near" vs. "far" pointers in win16 programming. But for the purposes of this article let's assume that an address is a byte offset into the whole address space.) Since addresses are just numbers you can easily perform pointer arithmetic with them.

Now consider C#, a language which has **both references and pointers**. There are some things you can only do with pointers, and we want to have a language that allows you to do those things (under carefully controlled conditions that call out that you are doing something that possibly breaks type safety, hence "unsafe".)  But we also do not want to force anyone to have to understand pointers in order to do programming with references.

We also want to avoid some of the optimization nightmares that languages with pointers have. Languages with heavy use of pointers have a hard time doing garbage collection, optimizations, and so on, because it is infeasible to guarantee that no one has an interior pointer to an object, and therefore the object must remain alive and immobile.

For all these reasons we do not describe references as addresses in the specification. The spec just says that a variable of reference type "stores a reference" to an object, and leaves it completely vague as to how that might be implemented. Similarly, a pointer variable stores "the address" of an object, which again, is left pretty vague. Nowhere do we say that references are the same as addresses.

So, in C# a reference is some vague thing that lets you reference an object. You cannot do anything with a reference except dereference it, and compare it with another reference for equality. And in C# a pointer is identified as an address.

By contrast with a reference, you can do much more with a pointer that contains an address. Addresses can be manipulated mathematically; you can subtract one from another, you can add integers to them, and so on. Their legal operations indicate that they are "fancy numbers" that index into the "array" that is the virtual address space of the process.

Now, behind the scenes, the CLR actually does implement managed object references as addresses to objects owned by the garbage collector, but that is an implementation detail. There's no reason why it has to do that other than efficiency and flexibility. **C# references could be implemented by opaque handles that are meaningful only to the garbage collector**, which, frankly, is how I prefer to think of them. That the "handle" happens to actually be an address at runtime is an implementation detail which I should neither know about nor rely upon. (Which is the whole point of encapsulation; the client doesn't have to know.)

I therefore have three reasons why authors should not explain that "references are addresses".

1. **It's close to a lie.** References cannot be treated as addresses by the user, and in fact, they do not necessarily contain an address in the implementation. (Though our implementation happens to do so.)

2. **It's an explanation that explains nothing to novice programmers.** Novice programmers probably do not know that an "address" is an offset into the array of bytes that is all process memory. To understand what an "address" is with any kind of depth, the novice programmer already has to understand pointer types and addresses -- basically, they have to understand the memory model of many implementations of C. This is one of those "it's clear only if it's already known" situations that are so common in books for beginners.

3. If these novices eventually learn about pointer types in C#, their confused understanding of references will probably make it **harder, not easier**, to understand how pointers work in C#. The novice could sensibly reason "If a reference is an address and a pointer is an address, then I should be able to cast any reference to a pointer in unsafe code, right?"  But you cannot.

If you think of a reference is actually being an opaque GC handle then it becomes clear that to find the address associated with the handle you have to somehow "fix" the object. You have to tell the GC "until further notice, the object with this handle must not be moved in memory, because someone might have an interior pointer to it". (There are various ways to do that which are beyond the scope of this screed.)

Basically what I'm getting at here is that **an understanding of the meaning of "addresses" in any language requires a moderately deep understanding of the memory model of that language**. If an author does not provide an explanation of the memory model of either C or C#, then explaining references in terms of addresses becomes an exercise in question begging. It raises more questions than it answers.

This is one of those situations where the author has the hard call of deciding whether an **inaccurate oversimplification** serves the larger pedagogic goal better than an **accurate digression** or a **vague hand-wave**.

In the counterfactual world where I am writing a beginner C# book, I would personally opt for the vague hand-wave.  If I said anything at all I would say something like "a reference is actually implemented as a small chunk of data which contains information used by the CLR to determine precisely which object is being referred to by the reference". That's both vague and accurate without implying more than is wise.

## References
1. [References are not addresses](https://blogs.msdn.microsoft.com/ericlippert/2009/02/17/references-are-not-addresses/)