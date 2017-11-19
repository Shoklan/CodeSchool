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
- We're going to split up the *main.ts* file into three parts:
  1. *main.ts*; only bootstrap and loading components.
  2. *app.component.ts* is where out page headers will be.
  3. *car-parts.components.ts* which will contain the data.
- To access the components you'll want to `export class AppComponents`.
- Then, we'll `import { AppComponents } from './app.component';`.
- The names in each file MUST BE THE SAME.
- When you import parts that are the the main AppComponent, make sure to add them as dependecies in `@NgModule`.
- This will give us access to `<car-parts></car-parts>` selector.
- To include css styles, we'll add `class="<style_identity>"`.
- Then, add them as a list:
```
styles: [`
  .description{
    //...
    }
  .price{
    //...
  }
    `]
```
- But, as we know, this all should be separate:
  * car-parts.component.html
  * car-parts.component.css
- Then, you tell it where those files are using `templateUrl : 'app/car-parts.component.html'` and `styelUrls: ['app/car-parts.component.css']`.
- We can now use *car-part.ts* to contain the template model for data.
- Make sure to export it!
```
export class carPartsComponent{
  carParts: CarPart[] ][{...}]
}
```
- *mocks.ts* is used to create *mock* data for testing.
- Instead of using a constructor, we'll use  `ngOnInit(){ this.carParts = CARPARTS;}`.
- `export const RACES: Race[] =`.

# Data Binding Boost
- We can include a *css* directory and can import from there; might need to do some splitting.
- We can also include an images folder too.
- **Property Binding** allows us to glue component properties to DOM element properties.
- `[src]`?
- This tells Angular to set this DOM property to out component property.
- And, if it is updated then Angular will auto update this value.
- Expample: `<div [hidden]="!user.isAdmin">Secret</div>`.
- **Class Property Binding** : `[class.featured]=carPart.featured` will enable the class css featured.
- **Dont' bind to class!**
- To start an event handler, we're define in *car-parts.components.ts* `upQuantity(carPart){carPart.quantity++}`
- To catch that event client side, we'll use `(click)="upQuantity(carPart)"`.
- We can also pass `showKey($event)`.
- To go both ways, we can create a binding going both ways or...
- In *main.ts* `import { FormsModule } from '@angular/forms';`.
- Then, we just include `[(ngModel)]="carPart.quantity"`.
- This is sometimes called **Banana-in-a-Box**.
- This can only be applied to data bound properties.

# Service Fuel Injection
- **Services** are used to organize and share code across your apps as well as create our data access models.
- We're going to use the file *racing-data.service.ts*.
- When you run an Angular Application, it creates a **Dependency Injector** which is in charge of knowing how to create and send things.
- To implement one:
  1. Add the injectable decorator to RacingDataService.
  2. Let our Injector know about the service.
  3. Inject it.
- To imort the injector: `import { Injectable } from '@angular/core';`.
- Place `@Injectable()` above the block.
- In *main.ts*, we're going to add `providers: RacingDataService` inside `@NgModule`.
- Inside *car-parts.components.ts* we're going to add `constructor( private racingDataService: RacingDataService){}`.
- Then, insde `ngOnInit(){ this.carParts = this.racingDataService.getCarParts();}`.
- We're going to request the data inside the service file.
- To use HTTP:
  1. Create a JSON file with car parts: *car-parts.json*
  2. Ensure it has libraries needed for http calls
  3. Tell the injector about the http provider.
  4. Inject the http dependency into service and make http get request.
  5. Listen for data returned by this request.
- We're going to be using **RxJS**, or Reactive Extentions JS.
- In *main.ts* we're going to `import {HttpModule} from '@angular/http';`.
- Then, add it to the list of imports.
- In *racing-data.service.ts* we'll `import { Http } from '@angular/http';`.
- In *racing-data.service.ts* we'll `import 'rxjs/add/operator/map';`.
- Build a constructor: `constructor( private http: Http){}`
- A couple final points:
  1. Make sure to add error handling.
  2. Go learn about **Observables**.
```
@Injectable()
export class RaceService {

  constructor(private http: Http){}

  getRaces() {
    return this.http.get('app/races.json')
  .map(response => <Race[]> response.json().racesData);
  }
}
```


## Reference:
- [Quick Start Guide](http://go.codeschool.com/angularstart).
-
