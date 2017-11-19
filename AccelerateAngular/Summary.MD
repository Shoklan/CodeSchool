# Accelerating Through Angular
## Gregg Pollack

# Angular Ignition
- Angular is a web framework for dynamic web applications
- It's a way to organize and ship your code efficiently.
- Angular is faster than Angularjs
- We use Components instead of controllers and scope.
- Directives are simpler.
- New Intuitive Data Bindings.
- Services are now just a class.
- **Babel** uses the latest features in JS, transpiles that into older JS.
- Or, **Typescript** which is a superscript of JS.
- Class uses *Typescript*.
- Developed by Microsoft.
- The files end is *.ts* instead of *.js*.
- We can leave the traspiling up the the browser or do it on the server.
- For production, do it ahead of time.
- Angular will load at `<my-app></my-app>`; this is name independent.
```js
System.import('app').
  catch(function(err){ console.error(err)});
```
- We're making out first Typescript file *app/main.ts*.
- In it, `import { Component } from '@Angular/core';`.
- `import` is an ES2015 new feature.
- A **Component** controls a certain portino of the webpage.
- A **Decorator Function** adds additional behavior to our class from outside our class.
- These two pieces will be:
```
@Component
class AppComponent
```
- The `@Component` is done to apply our component Decorator to our class.
- Then, it will use the `selector: 'my-app'` to tell it where to load.
- Then, `template: '<h1>Ultra Racing</h1>'` is where the content willbe placed.
- This is sometimes called the **Metadata**.
- **Modules** are how we orgainze our application.
- Every Angular app must have a root module.
- So, `import {NgModule,Component} //..` will be included at the top.
- And, we declare all our Components in the array:
```
@NgModule({
  declaration: [AppComponent]
  })
class AppModule{}
```
- Remember that ever decorator needs a matching class.
- Inside of `@NgModules` you will also need to mark `imports: [BrowserModule]` to tell it other required dependecies.
- `bootstrap: [AppComponent]` will tell us what component should be loaded first.
```
platformBrowserDynamic().
  bootStrapModule(AppModule);
```
- *Components* are the building blocks of our applications and they nest inside one another.
- Now that we have Components, we can start assigning stuff in them.
- In AppComponent, `title = 'Ultra Racing';`.
- We use interpolation to insert the data: i.e. `{{title}}` inside the component.
- We can do the same thing with arrays or lists.
- The whole context appears to be passed.
- Instead of using single quotes though we'll be using backticks; this is going to make documenting hell.

# Template Traction
- A **Directive** is how we add dynamic behavior to html.
- There are three kinds:
  1. Component Directives.
  2. Structural Directives.
  3. Attribute Directives.
- We create an iterator using `*ngFor="let carPart of carParts"`.
- A **Structural Directive** alters the layout by adding, removing or replacing html elements.
- You check if something is true using `<p *ngIf="carPart.inStock > 0">{{ carPart.inStock}} in Stock</p>`.
- We use **Pipes** to format.
- Example: `carPart | uppercase`; this is similar to filters in handlebars.
- To format currency, we use  ISO 4217; USD, EUR, CAD.
- You use it with `data.price | curreny:'EUR'`.
- You can chain options to add more: `data.price | curreny:'EUR:true'` will use the symbol for Euro.
- You can also just call methods using `{{totalCarparts()}}`.
- `of` is not the new `as` or `in` with ES2015.
- **BONUS**: `totalCarParts(){ return this.carParts.reduce(( prev, current), => prev + current.inStock, 0)};`.
```
totalCost(){
    let sum = 0;
    for( let race of this.races){
      if( race.isRacing) sum += race.entryFee;
    }
    return sum;
  }
```

# Tuning It Up
- 


# Data Binding Boost

# Service Fuel Injection

## Reference:
- [Quick Start Guide](http://go.codeschool.com/angularstart).
-
