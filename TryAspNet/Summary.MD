# Try ASP.NET Core
## Eric Fisher

# Model View Controller
- ASP.NET is a framework for the rapid development of Web Applications.
- It helps to keep the code clean and easy to maintain.
- It can run on any OS.
- Handles everything from the UI to the server.
- Data Flow Model:
  1. User input into Browser.
  2. Controller accepts the request.
  3. Controller accesses data in the model.
  4. Controller passes the data to the View.
  5. The View is then presented back to the user.
- The default folder structure contains:
  * Models
  * Views
  * Controllers
- The names of files are important.
- The **cshtml** file is a template file that is used by our apps.
- To update this file, we need the view to accept the data and a controller to send it.
- We'll add `@model String` to let it know we expect an incoming string.
- The engine that's used to do this is called *Razor*.
- To use the passed data, you now pass `@Model`; notice the upper case.
- The case of the variables defines where this is data sent or data accessed.
- The *Controller* is split into three sections:
  1. The Namespace.
  2. The Class.
  3. The Method.
- *Methods* should return an *IActionResult* is for a response to the browser.
- To return the data, use `return View("Index", <data>)`.
- **Routes** are how our app decides what controller and what actions take place.
- Via the Controlle file, the controller maps to the Index.
```
public class HomeController : Controller{
  public IAction Index(){
    return View();
  }
}
```
- With **Default Routes**, we can control where the user gets directed most of the time.
- Variables in our Models should be in Pascal Case.
- With this new field, we can initialize a new Character Model and assign the name.
- Each namespace will be contained to `<AppName>.{Models|Views|Controllers}`.
```
var model = new CharacterSheetApp.Models.Character();
```
- Then, in the View we change the include to `@model CharacterSheetApp.Models.Character`.
- And, change the data field to `@Model.Name`.

# Getting User Input
- 



# Retaining Data
