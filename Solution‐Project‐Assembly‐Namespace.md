> *前言：表弟想要学编程，我推荐他学习.Net和C#。这一推荐不打紧，我却承担上了指导的职责。我又出差在外，直接辅导是不行了，通过邮件也太麻烦。推荐了几本书，可惜他太菜了，总有无从下手的感觉。推及他人，在初学C#时，是否也有这样的感觉呢？所以，就有了这个系列文章。表弟是我把他带入计算机行业的，当初什么都不懂，我曾经打开计算机机箱，指点他哪里是硬盘、哪里是内存，是CPU，现在对于计算机硬件他早已可以做我师傅。希望学软件编程也能这样。*

## 解决方案、项目、程序集、命名空间

初学者很容易把这些概念搞混淆。先说说项目（Project），通俗的说，一个项目可以就是你开发的一个软件。在.Net下，一个项目可以表现为多种类型，如控制台应用程序，Windows应用程序，类库（Class Library），Web应用程序，Web Service，Windows控件等等。如果经过编译，从扩展名来看，应用程序都会被编译为.exe文件，而其余的会被编译为.dll文件。既然是.exe文件，就表明它是可以被执行的，表现在程序中，这些应用程序都有一个主程序入口点，即方法Main()。而类库，Windows控件等，则没有这个入口点，所以也不能直接执行，而仅提供一些功能，给其他项目调用。

在Visual Studio.Net中，可以在“File”菜单中，选择“new”一个“Project”，来创建一个新的项目。例如创建控制台应用程序。注意在此时，Visual Studio除了建立了一个控制台项目之外，该项目同时还属于一个解决方案（Solution）。这个解决方案有什么用？如果你只需要开发一个Hello World的项目，解决方案自然毫无用处。但是，一个稍微复杂一点的软件，都需要很多模块来组成，为了体现彼此之间的层次关系，利于程序的复用，往往需要多个项目，每个项目实现不同的功能，最后将这些项目组合起来，就形成了一个完整的解决方案。形象地说，解决方案就是一个容器，在这个容器里，分成好多层，好多格，用来存放不同的项目。一个解决方案与项目是大于等于的关系。建立解决方案后，会建立一个扩展名为.sln的文件。

在解决方案里添加项目，不能再用“new”的方法，而是要在“File”菜单中，选择“Add Project”。添加的项目，可以是新项目，也可以是已经存在的项目。

程序集叫Assembly。学术的概念我不想提，通俗的角度来说，一个项目也就是一个程序集。从设计的角度来说，也可以看成是一个完整的模块（Module），或者称为是包（Package）。因此，一个程序集也可以体现为一个dll文件，或者exe文件。怎样划分程序集也是大有文章的，不过初学者暂时不用考虑它。

命名空间（namespace）是在C++里面就有的概念。引入它，主要是为了避免一个项目中，可能会存在的相同对象名的冲突。这个命名空间的定义，没有特殊的要求。不过基本上来说，为了保证其唯一性，最好是用uri的格式，例如BruceZhang.com。这个命名空间有点像我们姓名中的姓，然后每个对象的名字则是姓名中的名。如果有重复，再国外的命名中，还可以加上middle name。那么名都为勇的，由于姓氏不同也就分开了，或者叫张勇，或者叫赵勇。当然人的姓氏重复者居多，所以我们为命名空间取名时，尽可能的复杂一点。

有许多初学者，常常把一个项目就理解为一个命名空间。其实这两者没有绝对的联系，在项目里我们也可以定义很多不相同的命名空间。但为了用户便于使用，最好在一个项目中，其命名空间最好是一体的层次结构。在Visual Studio里，我们可以在项目中新建一个文件夹，默认情况下，该文件夹下对象的命名空间，应该是“项目的命名空间.文件夹名”。当然，我们也可以在namespace中修改它。

命名空间和程序集名，都可以在Visual Studio中设置。用鼠标右键单击项目名，就可以弹出如下对话框：

![](img/Solution-Project-Assembly-Namespace/fig1.gif?raw=true)

在图中，Assembly Name就是程序集名，如果经过编译，则为该项目的文件名。而Default Namespace则为默认的命名空间。在开发软件时，我们要养成良好的习惯，在建立新项目后，就将这些属性设置好。一旦设置好了Default Namespace，则以后新建的对象，其命名空间即为该设定的值。至于程序集名，如果是dll文件，建议其名最好与Default Namespace一致。

## 实例演练：

#### 创建控制台应用程序“Hello World!”
1. 打开Visual Studio.Net，选择“File”菜单的“new”，选择“Project”；
2. 选择Visual C# Projects中的“Console Application”，在Location中，定位你要保存的项目的路径，而名字则为“FirstExample”。该名字此时既是解决方案的名字，同时也是该项目的名字。

	![](img/Solution-Project-Assembly-Namespace/fig2.gif?raw=true)

3. 用鼠标右键单击项目名，在弹出的对话框中，将Assembly Name命名为HelloWorld，将Default Namespace命名为：BruceZhang.com.FirstExample。
4. 此时Visual Studio中已经建立了一个文件，其名为Class1.cs（如果是Visual Studio 2005，则默认为Program.cs）；修改该文件的文件名为HelloWorld.cs，同时修改文件中的namespace，和类名，如下：

	```c#
	namespace BruceZhang.com.FirstExample
	{
	 /// <summary>
	 /// Summary description for Class1.
	 /// </summary>
	 class HelloWorld
	 {
	  /// <summary>
	  /// The main entry point for the application.
	  /// </summary>
	  [STAThread]
	  static void Main(string[] args)
	  {
	   //
	   // TODO: Add code to start application here
	   //
	  }
	 }
	}
	```

5. 注意在HelloWorld.cs中，有一个Main()方法。这是因为我们建立的是控制台应用程序。在Main()方法中添加如下代码：
	```c#
	Console.WriteLine("Hello World!");
	Console.Read();
	```
6. 运行。

检查保存项目的路径文件夹FirstExample/bin/debug，已经存在了一个HelloWorld.exe文件。

#### 为解决方案添加一个新项目
1. 在“File”菜单中，选择“Add Project”，添加“New Project”。在对话框中选择“Class Library”，名字为Printer。至于保存路径，可以放在之前建立的FirstExample文件夹下：

	![](img/Solution-Project-Assembly-Namespace/fig3.gif?raw=true)

2. 在Visual Studio右侧，可以看到现在有两个项目了。仍然修改新项目的名称和默认命名空间名，均为BruceZhang.com.Printer。
3. 将默认建立的Class1.cs改名为MessagePrinter.cs，同时修改其代码。在MessagePrinter类中，我们注意到并没有Main()方法，因为它不是应用程序。新增加的Print()方法，能够接收一个字符串，然后在控制台中显示出来。

	```c#
	namespace BruceZhang.com.Printer
	{
	 /// <summary>
	 /// Summary description for Class1.
	 /// </summary>
	 public class MessagePrinter
	 {
	  public MessagePrinter()
	  {
	   //
	   // TODO: Add constructor logic here
	   //
	  }
	  public static void Print(string msg)
	  {
	   Console.WriteLine(msg);
	  }
	 }
	}
	```

4. 编译Printer项目。鼠标右键单击该项目名，在菜单中选择“Build”。成功编译后，找到文件夹Printer/bin/debug，可以发现有文件BruceZhang.com.Printer.dll，这就是最后形成的程序集文件。
5. 关联这两个项目。我们希望是在FirstExample项目中用到Printer项目的Print()方法，前提是需要在FirstExample项目中添加对Printer项目的引用。右键单击FirstExample项目的“Reference”，选择“Add Reference”，在对话框中选择“Project”标签，找到该项目并选中，最后如图所示：

	![](img/Solution-Project-Assembly-Namespace/fig4.gif?raw=true)

6. 现在就可以在FirstExample项目中使用MessagePrinter了。首先，在命名空间中添加对它的使用（Using），然后再Main()方法中调用它，最后代码如下：

	```c#
	using System;
	using BruceZhang.com.Printer;
	namespace BruceZhang.com.FirstExample
	{
	 /// <summary>
	 /// Summary description for Class1.
	 /// </summary>
	 class HelloWorld
	 {
	  /// <summary>
	  /// The main entry point for the application.
	  /// </summary>
	  [STAThread]
	  static void Main(string[] args)
	  {
	   MessagePrinter.Print("Hello World!");
	   Console.Read();
	  }
	 }
	}
	```

7. 运行。结果与前一个例子一样。

在这个例子中，解决方案中就包含了两个项目，一个是控制台应用程序，一个是类库。类库提供一些基本的功能，如例子中的Print()方法。我们常常把一些共用的方法，放到类库中。这样其他的应用程序就可以去调用它。例如本例的控制台应用程序。如果新建的Windows应用程序，也需要这个功能，就可以直接引用MessagePrinter的Print()方法，而不必重复去实现。

## References

1. [解决方案、项目、程序集、命名空间](http://www.cnblogs.com/wayfarer/archive/2006/04/07/369371.html)
<!--stackedit_data:
eyJoaXN0b3J5IjpbODU3NDYzNjE3XX0=
-->