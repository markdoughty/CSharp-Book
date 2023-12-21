# Introducing C#

> "Introducing C#"
>
>> *Why do Java programmers have to wear glasses? Because they don’t C#.* <sub>Anon</sub>

1. [Why use C#?](#why)
2. [Programming C# - the IDE](#programming)
3. [First C# code](#first)

<a name="why"></a>
#### Why use C#?

- It is (relatively) easy to learn and use
- C# is an *object oriented language* which gives a clear structure to programs and allows code to be reused.
- As C# is a close relative  to C, C++ and Java, it makes it easy for programmers to switch between them.

<a name="programming"></a>
#### Programming C# - the IDE

An IDE (Integrated Development Environment) provides many facilities and functions for software development. For C#, I will use [Visual Studio](https://visualstudio.microsoft.com/) and examples will be shown in this form, however, many more IDEs for C# development exist. For example:

- [Visual Studio Code](https://code.visualstudio.com/)
- [Mono Develop](http://www.monodevelop.com/)
- plus many more.

We can write C# code (and saving the file with the ```.cs``` extension) with any text editor, such as notepad, notepad++, vim, vi, etc.

To compile code written with a text editor, you need to make sure you have a C# compiler installed.

It is easier if you don't want the footprint of an IDE on your computer to use online code editors and compilers:

- [.NET Fiddle](https://dotnetfiddle.net/)
- [replit](https://replit.com/languages/csharp)
- plus many more.

<a name="first"></a>
#### First C# code
The best way to start to look at C# and how it works, is to look at some code which solves a problem.

Imagine you have a fabric shop and want to quickly work out how much a piece of fabric a customer orders will be.

The inputs will be:
- Length (m)
- Fabric Price (£/m)
~~~
	using System;
	using System.Collections.Generic;
	using System.Linq;

	public class Fabric {
		public static void Main (string[] args) {
			double length;
			double pricePerMetre, totalPrice;

			Console.WriteLine("What is the length in metres?");

			length = Double.Parse(Console.ReadLine());

			Console.WriteLine("What is the price per metre?");

			pricePerMetre = Double.Parse(Console.ReadLine());

			totalPrice = length * pricePerMetre;

			Console.WriteLine("The total price is " + totalPrice);
		}
	}
~~~

Each line of the code does something specific and is important to the C# compiler to build the executable properly and make it run.

`using ...`

These specify which namespaces or 'libraries' are made available to your code. There are three here which are included by default. The 'System' namespace contains the 'Console' class, which means we can use methods (such as 'WriteLine') from the Console class.

`public class ...`

The 'public' access qualifier, means that the class is able to be used by everyone. There will be more on these access qualifiers later.

A class in C# is a 'blueprint' or 'plan' for creating objects. In C#, everything has to be defined within a class. A C# program can contain many classes (or just one!). A class defines a 'thing', and defines everything which describes that 'thing'. For instance, there may be 'attributes', 'properties', 'methods' (which describes the functionality of the thing), etc.

Following 'class' is its name - or 'identifier'. This should be unique, and ideally the 'thing' the class refers to. In this case the class is called `Fabric`.

`public static void Main (string[] args) {`

`static` in this case, means that the method called `Main` belongs to the class description, and that only one copy of `Main` will exist, regardless of how many objects are made (or 'instantiated') from the class. For `Main` to work here, it must be described as `static`.

`void` here, means that the method called `Main` produces no output. The method runs but doesn't produce a result or outcome. The term used is it 'returns' nothing. Later, we will look at methods which do 'return' an output. If we don't intend a method to return anything, then the `void` qualifier must be used.

`Main` is the name, or 'identifier' of the method. In any other case we can choose the identifier for a method, however, for `Main`, the method has to be called this. This is because when the program runs, a method called `Main` is looked for to run from the start, as this is the 'entry point' for the application.

`(string[] args)` has two enclosing brackets '( .. )'. These can be empty, but also have what we have got here. The two brackets define what 'parameters', data or 'arguments' are used by the 'Main' method. These brackets can be empty (indicating the Main method uses no parameters), or as we have here, which indicates how those parameters can be defined - but there can still be none (this shows parameters defined as an array of string variables called 'args').

`{ .. }` These are called 'braces' and define a code 'block'. Braces are used to enclose a block of code, such as a method, a loop, a conditional statement, or a class. They determine the beginning and end of the block, providing a clear visual indication of where the block starts and ends. This helps maintain code organization and readability. Braces define the 'scope' or 'visibility' of variables and objects, etc.

`double` defines the type of data which the variable called 'length' can hold. Think of the data type as a size and shape of bucket which 'length' is stored in. Only buckets of the correct size and shape will be able to accomodate 'length'. There are many data types (or bucket sizes) in C#. Some of these are:

- `int` 32 bit integer (a whole number)
- `float` floating point number (an integral or decimal number)
- `double` double precision floating point number (twice the size of `float` values
- `string` a sequence of zero or more unicode characters.
- and lots more!

So, in this case, if you try to put `string` data into 'length', it will create a problem, as `string` data will not fit into a `double` sized bucket.

`;` The semi-colon is very important to C# code (and many other languages) in that is defines the separation of all the statements. This is for many reasons, primarily, it informs the compiler when each statement is terminated, and helps to organise and structure the code visually.

`Console.WriteLine` This indicates that we intend to use the `WriteLine` method which is in the `Console` class. The 'WriteLine' method takes the `string` data inside the following brackets, and outputs it to the console screen. The `string` data is defined between the 'speech marks'. We can make this more complex by adding formatting data and variable names.

`Double.Parse` Converts whatever follows it within the brackets from a `string` to a `double`. This only works if the `string` is a value which can be converted to a `double`. For example, "3.56" will be converted to 3.56.

`Console.ReadLine` is a point in the code where it waits for input from the user. i.e. it waits for the user to type something into the console. This method always produces a `string`, so if we ask the user for a number, we will have to subsequently concert this number from a `string` to whichever data type we want (like the `Double.Parse` here).

`totalPrice = length * pricePerMetre;` This is the point in the program where the data we entered or defined is used to do some calculations. We could say, that an 'algorithm' is used here.

This line has two operators `*` and `=`. The `*` is the multiplication operator, and means that the two values held by `length` and `pricePerMetre` are multiplied together. The result of this multiplication is then put into, or 'assigned' using the `=` operator to the `totalPrice` variable. One thing to remember here, is that `=` is the 'assignment operator' and not as we might say in mathematics 'equal to'. We will look at the 'equality operator' (`==`) later.

`Console.WriteLine("The total price is " + totalPrice);` This line writes out some `string` data ("The total price is "), and then uses one method (there are a few) to add the value held by the `totalPrice` variable to the end of the string. Here the `+` operator is used to do this and means in this case 'append' to the end of the string.

When you run the code, the 'code flow' starts at the entry point (i.e. the start of the `Main` method) and flows downwards through the code, executing each 'statement' (defined by the semi colons) in turn.