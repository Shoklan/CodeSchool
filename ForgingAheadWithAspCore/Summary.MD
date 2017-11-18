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
- Before we can implement the data structure, we need to plan it out.
- A database manages a *many-to-many* relationship is with a **Union Table**.
- All we need to really do is add a property list of the equipment to our character class.
```
public List<Character> Characters { get; set;}
```
- Now we're going to manage our views:
  1. Index.cshtml
  2. Create.cshtml
- To manage links, you include `asp-action="<Action> asp-controller="<Class>" ` to the *<a>* elements.
- To control passing inputs to the Controller, you use `asp-route-name="@item.name"` in the *<a>* element.
- This will add a query string to the url when it is clicked.
- On the recieving page, you'd tag the variable in `asp-for="Name"` in both label and input.
- To start using **Data Annotations** you'd need `using System.ComponentModel.DataAnnotations;` in the class file.
- Then, in the class definition you'd use `[Display(Name = "Is Active")]` after setting the properties.

# Making Our Presentation Smarter
- The **_Layout.cshtml** file is found in Views > Shared and controls the layout of the app.
- The App knows which views to use since they're defined in **_ViewStart.cshtml**.
- Inside the *_Layout.cshtml* file:
  * `@ViewData["Title"]` is a dictionary that allows us to pass data from the view to the model.
  * `@RenderSection("header", required: false)` means to insert the header file info here but you don't have to.
  * `@RenderBody()` is where most of our changes have been inserted.
- We can change `@ViewData` as if it's a variable in the Controller file.
- For `@RenderHeader` that is inserted in *Index.cshtml*.
```
@section_header{
  <meta name ...
}
```
- Everything inside the braces will get inserted.
- Naming nomenclature is *_PascalCase* for those files.
- Layouts typically go in the *Shared* folder.
- Sections names should be all lower case.
- Don't include info that is only in some pages.
- We can creat what are called **Partials** and share those between pages.
- It's just basically another view.
- We'll then define the partial at the top using `@Html.Partial("_CharacterSheet", Model)`.
- You can place the partials in either the shared folder or organized by model.
- `@Html.EditorForModel()` insert the correct fields and labels based on the model passed.
- You can override parts of the templates to make them visually better.
- To do this, you need an **EditorTemplates** folder in the *Shared* folder.
- The subfiles are named after the types that could be passed:
  + *Boolean.cshtml*
  + *Int32.cshtml*
  + etc.

# Creating Logical URLs
- We can use custom routes to make urls easier to remember.
- Ther are two places where the custom routes are set up:
  1. *Startup.cs*
  2. Specific Actions.
- To do this in specific cases, you navigate to the Controller file and `[Route("Character/{name}/Details")]`.
- This gets put into the class but above actions.
- **GET*** and **POST** are examples of **HTTP Verbs**
- You can force a Controller to only accept one using `[HttpGet]` or `[HttPost]`.
- **Http DELETE** exists but most browswer don't use it.

# Validating Our Input
- You can mark fields are `[Required]` in the Controller.
- To include annotations, we're going to need `using System.ComponentModel.DataAnnotations;`.
- You can mark a field as the primary key using `[Key]`.
- You can force a length constraint using `[MinLength(<n>)]`.
- You can set a limited range of accepted numbers using `[Range(1,18)]`
- Front End Validation is the fastest and most convenient.
- We're going to be using *JQuery-validation* and *JQuery-validation-unobtrusive*
- We just needed to add the references in the layout.
- To display this, we need to add `<div asp-validation-summary="All"></div>` to the input View.
- The name for backend validation is **ModelState Validation**.
- The *Modelstate* is a property that tracks the data submitted to the server.
```
if(!ModelState.IsValid)
  return View(character);
```
- If you leave the name check until it hits the database, then you get a blank page on the redirect.
```
if(_context.Characters.Any( e => e.Name == character.Name))
  ModelState.AddModelError("Name", "Name is already taken.");
```
- The error messsages passed back are pretty useless when you have lots of fields.
- You can solve this by using `[Required(ErrorMessage = "The attribute field is required")]` in the Models file.
