# Keeping it Classy with C#
## Eric Fisher

# Methods
- All projects have a *.csproj* file, which I missed from the last class.
- To create a method, we're going to need a *name* as well as *parameters* for it.
- Method names should use **Pascal Case**.
- *Parameters* should be prefixed with the data type.
- Methods also require a *return type* and a *Return Statement*.
- To call a method, we use its name along with the necessary parameters.
```
string announcement = AnnounceBand("The C Sharp");
```
- Methods that do not return anything should use the **void** return data type.

# Classes
- The **Class** defines the structure of the object.
- While the **Object** is the instance of the class.
- To declare a class we use the format `class <class_name> `.
- It's standard nomenclature to call the file what we're going to call the class inside it.
- The variables declared inside a class are called **Instance Variables**.
- Each individual object, or instance, has its own *instance variables*.
- **Namespaces** are used to organize classes to allow for reuse.
- *Namespaces* can be accessed using the format `Namespace.Class.Method`.
- You can shorten this using what is called a **Directive**.
```
using System;
// using System.Console
```
- You can create a new instance using the format `new <Class>()`.
```
<Class> <instance_name> = new <Class_name>()
```
- **Protection Levels** are set by what are known as *Access Modifiers*.
- The *public accessor* allows the variable to be accessible anywhere.
- The *private accessor* allows the variable to be accessible only in the class.
- The default mode is private.

# Groups of Objects
- The **Object Initializer** allows us to declare and initialize the objects variables in a single line.
```
<Class> <instance_name> = new <Class_name>{ <arg1> = <par1>, <arg2> = <par2>};
```
- There are several ways to group objects, but we're only going to cover two:
  1. Arrays
  2. Lists
- To initialize an array of type object, use:
```
<Class>[] <array_name> = new <Class_name>[<n>];
```
- It uses normal array indexing.
- *Arrays* are of a fixed size.
- *Lists* are better when we don't know how many objects there will be.
- To initialize a list, use:
```
List<Class> <array_name> = new List<Class>();
```
- You add to lists using `list_name.Add{ <initialized_object_here }`.
- To use lists we'll need to include `using System.Collections.Generic;`
- If you don't want to deal with types, then `var` will try and guess it.
- **Null** is the absence of a value; not an empty value.
- We can make sure that the initialized list is empty but is still a list.
```
public List<class_name> <instance_name> = new List<class_name>();
```

# Loops
- A **While Loop** will continue until the *break* keyword is used or the condition is false.
- Format:
```
while( <var> ){
  // do stuff here
}
```
- If you there is no condition to escape the loop, then you have an *infinite loop*.
- `break` will immediately exit the loop.
- A **Foreach Loop** will iterate through each object and run code for each one.
```
foreach( var item in Objects){}
```

# Method Overloads
- 
