# Try C#
## Erik Fisher

# What is C#?
- .. is a general purpose object-oriented programming language released by Microsoft in 2002.
- Characteristics:
  * Compiled.
  * Strongly Typed.
  * .Net language; allows us to mix C#, F#, VB.Net
- Create a new program using `dotnet new console`.
- All modern C# programs will start in the *Program.cs* file.
- **Classes** allow us to separate our code into objects.
- **Methods** contain the executable code.
- Execution will start at the *Main function*.
- `Console.WriteLine()` will print what we pass to the console.
- Before running program, use `dotnet restore` to manage dependencies.
- This needs to be run before our first run as well as when dependencies change.
- You can run the program using `dotnet run`
- To read input, you use `Console.readLine()`.

# Variable
- **Variables** allow us to store information in memory for use later.
- To use a variable, you need to declare it.
- The declaration requires the *datatype* of the variable and then the *name* of it.
- **=** is the *assignment operator* as per normal.
- There are *15* different built in data types.
- We can convert a string to an integer use the `int.Parse()` method.

# Changing the Flow of Our Application
- When a user enters something we didn't expect, then we get an error.
- To handle this, we can use `int.TryParse()` instead.
- Some methods having something called an *output parameter* which is not that common.
- `int.TryParse()` happens to have one.
```
int.TryParse( Console.ReadLine(), out numberOfMembers)
```
- We're going to use the `if(){}` block to test.
- `!` is the unary operator for logical not.
- We can tell the program to exit with successful completion using `Environment.Exit(0)`.
- I know what the `if-else` blocks are.

# Reference:
- [Install C#](www.go.codeschool.com/install-dot-net)
