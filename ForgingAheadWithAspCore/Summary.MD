# Forging Ahead with ASP.NEt Core
## Eric Fisher

# Engaging your Data
- There is ASP.NET Core and ASP.NET Framework; we're working with Core.
- Directives will use *core*.
- For storing data long term, we have two choices:
  1. Filesystem.
  2. Database.
- For this, all of our business and data logic will go in a model.
- To read from a database, we'll need a *ApplicationDbContext,cs*.
- We will need:
  * Reference to Entity Framework.
  * Add a property to Character.
  * Create a CharacterController to load the context.
  * Create a character via that context.
  * Save the charcter in the DB.
- To include the *EntityFramework* we will `using Microsoft.EntityFrameworkCore;`.
- This will allow us to inherit the *DbContext Class*.
- We'll be using a *DbSet Collection* which is sort of like a list.
```
public DbSet<Character> Characters {get; set;}
```
- The *DbSet* is supposed to be plural form of your class in the set.
- For the Controller, we'll need `using Microsoft.AspNet.Core.Mvc;`.
- For the Controller, we'll need `using Microsoft.EntityFrameworkCore;`.
- For the Controller, we'll need `using System.Collections.Generic;`.
- For the Controller, we'll need `using <app_name>.Models;;`.
- We'll want a private context variable: `private readonly ApplicationDbContext _context;`.
- The nomenclature about a private readonly variable is to lead it with an underscore.
```
public CharacterController( ApplicationDbContext _context){
  context = _context;
}
```
- This is called **Dependency Injection** since we're using an already existing instance instead of creating a new one.
- The purpose of *Dependency Injection** is to achieve the inversion of control.
- We can now reference `_context` when making changes.
- The difference is that every time we make a change, we need to call `_context.SaveChanges();`.
- Then, make sure to redirect to avoid allowing the user to resubmit data.
- *Entity Framework* is an **Object-Relational Mapper**.
- **CRUD** stands for *Create, Read, Update, Delete*.
- To tell our project how to use the ORM, we'll add the details toe the *Startup.cs* file.
- This file is to configure our application to use all these frameworks.
- The Injection details go in `ConfigureServices()`.
```
public void ConfigureServices( IServiceCollection services){
  services.AddEntityFramework().AddDbContext<Models.ApplicationDbContext>();
  services.AddMvc();
}
```
- You can add lambda expressions by the directive `using System.Linq;`.
```
public IActionResult(){
  var model = _context.Characters.ToList();
  return View( model );
}
```
- Now we're going to see lambda expressions:
```
public IActionResult GetActive(){
  var model = _context.Characters.Where( e => e.isActive).ToList();
  return View( model );
}
```
- To get the details of a character, you'll use `.FirstOrDefault( e => e.Name == name)` in the *_context.Characters* call.
- To update the details of a character, you'll use `_context.Entry( character ).State == EntityState.Modified;`.
- Don't forget to save the changes.
- To remove, you use `_context.Characters.Remove( <whatever_model> )`.

# Showing Off Your Data

# Making Our Presentation Smarter

# Creating Logical URLs

# Validating Our Input
