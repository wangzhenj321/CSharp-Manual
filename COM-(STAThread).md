## The Component Object Model

The Microsoft Component Object Model (COM) is a platform-independent, distributed, object-oriented system for creating binary software components that can interact. COM is the foundation technology for Microsoft's OLE (compound documents), ActiveX (Internet-enabled components), as well as others.

To understand COM (and therefore all COM-based technologies), it is crucial to understand that it is not an object-oriented language but a standard. Nor does COM specify how an application should be structured; language, structure, and implementation details are left to the application developer. Rather, COM specifies an object model and programming requirements that enable COM objects (also called COM components, or sometimes simply *objects*) to interact with other objects. These objects can be within a single process, in other processes, and can even be on remote computers. They can be written in different languages, and they may be structurally quite dissimilar, which is why COM is referred to as a *binary standard*; a standard that applies after a program has been translated to binary machine code.

The only language requirement for COM is that code is generated in a language that can create structures of pointers and, either explicitly or implicitly, call functions through pointers. Object-oriented languages such as C++ and Smalltalk provide programming mechanisms that simplify the implementation of COM objects, but languages such as C, Java, and VBScript can be used create and use COM objects.

COM defines the essential nature of a COM object. In general, a software object is made up of a set of data and the functions that manipulate the data. A COM object is one in which access to an object's data is achieved exclusively through one or more sets of related functions. These function sets are called *interfaces*, and the functions of an interface are called *methods*. Further, COM requires that the only way to gain access to the methods of an interface is through a pointer to the interface.

Besides specifying the basic binary object standard, COM defines certain basic interfaces that provide functions common to all COM-based technologies, and it provides a small number of functions that all components require. COM also defines how objects work together over a distributed environment and has added security features to help provide system and component integrity.

## Thread.ApartmentState Property

The ApartmentState property is obsolete. The non-obsolete alternatives are the GetApartmentState method to retrieve the apartment state and the SetApartmentState method to set the apartment state.

In the .NET Framework versions 1.0 and 1.1, the ApartmentState property marks a thread to indicate that it will execute in a single-threaded or multithreaded apartment. This property can be set when the thread is in the Unstarted or Running thread state; however, it can be set only once for a thread. If the property has not been set, it returns Unknown.

An attempt to use the ApartmentState property to set the apartment state of a thread whose apartment state has already been set is ignored. However, the SetApartmentState method throws a InvalidOperationException in this case.

> In the .NET Framework version 2.0, new threads are initialized as ApartmentState.MTA if their apartment state has not been set before they are started. The main application thread is initialized to ApartmentState.MTA by default. You can no longer set the main application thread to ApartmentState.STA by setting the System.Threading.ApartmentState property on the first line of code. Use the STAThreadAttribute instead.

## Could you explain STA and MTA?

The COM threading model is called an "apartment" model, where the execution context of initialized COM objects is associated with either a single thread (Single Thread Apartment) or many threads (Multi Thread Apartment). In this model, a COM object, once initialized in an apartment, is part of that apartment for the duration of its runtime.

The STA model is used for COM objects that are not thread safe. That means they do not handle their own synchronization. A common use of this is a UI component. So if another thread needs to interact with the object (such as pushing a button in a form) then the message is marshalled onto the STA thread. The windows forms message pumping system is an example of this.

If the COM object can handle its own synchronization then the MTA model can be used where multiple threads are allowed to interact with the object without marshalled calls.

## Why is STAThread required?

When the STAThreadAttribute is applied, it changes the apartment state of the current thread to be single threaded.  Without getting into a huge discussion about COM and threading, this attribute ensures the communication mechanism between the current thread and other threads that may want to talk to it via COM.  When you're using Windows Forms, depending on the feature you're using, it may be using COM interop in order to communicate with operating system components.  Good examples of this are the Clipboard and the File Dialogs. 

Windows Forms is not supported within a MTA or free threaded apartment.  Applications using Windows Forms should always declare the apartment style they're using, as some other component could initialize the apartment state of thread improperly. 

## References
1. [The Component Object Model](https://msdn.microsoft.com/en-us/library/windows/desktop/ms694363(v=vs.85).aspx)
2. [Thread.ApartmentState Property](https://msdn.microsoft.com/en-us/library/system.threading.thread.apartmentstate%28v=vs.110%29.aspx?f=255&MSPPError=-2147217396)
3. [Could you explain STA and MTA?](https://stackoverflow.com/questions/127188/could-you-explain-sta-and-mta)
4. [Why is STAThread required?](https://blogs.msdn.microsoft.com/jfoscoding/2005/04/07/why-is-stathread-required/)