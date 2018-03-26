#### wrapper
A  [wrapper](http://en.wikipedia.org/wiki/Wrapper_library)  is a bit of code that sits on top of other code to recycle it's functionality but with a different interface. This usually implies an interface written in the same language. It should also be noted that sometimes people will say wrapper when what they technically mean is a binding (myself included).

Pros:

-   It's in the same language as the original
-   Wrappers enhance or reuse functionality without needing a full rewrite.
-   Relatively quick to accomplish
-   Trivial updates when the source library changes. You'll probably only need to bind new functions unless they broke backwards compatibility by changing expected input/outputs of functions/classes.

Cons:

-   Wrapping an entire library can be extremely repetitive

#### binding
A  [binding](http://en.wikipedia.org/wiki/Language_binding)  is another bit of code that sits on top of other code to recycle it's functionality except this time bindings are written in a language different than the thing they bind. A notable example is PyQt which is the python binding for QT.

Pros:

-   Bring functionality from another language into the language of your choice.
-   Relatively fast in comparison to a port
-   Same level of trivial changes are needed as in wrapping- You'll probably only need to wrap new functions/classes unless they broke backwards compatibility by changing expected input/outputs of functions/classes.

Cons:

-   Just as repetitive as a wrapper
-   You're probably taking a fairly large performance hit, especially any wrapper involving an interpreted language on either end

#### port
A  [Port](http://en.wikipedia.org/wiki/Porting)  is when you translate some code to work in a different environment. Common analogies include games that come out for say... XBox and are later released for PS3.

Pros:

-   Gives you the opportunity to make improvements to the code base as you see inadequacies
-   You'll be intimately familiar with HOW the code runs, not just what it does.

Cons:

-   By far the lengthiest solution in terms of time/requires a complete rewrite
-   You need to make sure that whatever functionality the source library needs in a language is available in your target port language or you'll end up wrapping needed functionality (and potentially defeating the purpose.)
-   Every time the source library updates, you have to update too by translating whatever changes they made or risk falling behind.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExOTgyMDU2MzZdfQ==
-->