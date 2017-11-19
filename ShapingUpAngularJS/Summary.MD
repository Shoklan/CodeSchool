# Shaping Up With AngularJS
## Gregg Pollack

# Flatlander's Gem Store
- The Programmingg world is moving towards only sending preciesly what changes using an API.
- **AngularJS** is a client-side Javascript Framework for adding interactivity to HTML.
- A **Directive** is a marker on a HTML tag that tells Angular to run or reference some Javascript.
- You match `ng-controller` tags with the function in the javascript.
- Angular **modules** are where we keep our Angular code to keep it easier to maintain.
```js
var app = angular.module('store', []);
// where angular.module to create a new module
// 'store' is the name of fthe new module.
// [] are the dependencies
```
- This will be included in an *app.js* file which will need to be added to the webpage.
- Then, you will need to add `<html ng-app='store'>`.
- **Expressions** are how you insert dynamic values into your HTML.
- **Controllers** are where we define our apps behavior by defining functions and values.
- You attach the controller directive to a div: `<div ng-controller="StoreController as store">`.
- You'll then insert `{{store.product.name}}` to insert the value; store is just an alias here and can be changed.
```js
(function(){
  var app = angular.module('store', []);

  app.controller('StoreController', function(){
    this.product = gem;
  });

  var gem = {
    name: 'Dodecahedron',
    price: 2.95,
    description: '...',
  }
})();
```
- You can use a logical value to control whether something is displayed.
- This is done with `<button ng-show="store.product.canPurchase">`.
- If the referenced value does not exist then Angular assumes it is false.
- You can also use `ng-hide` to make it easier to read.
- To iterate over values, you use the `ng-repeat="product in store.products"`.

# Built-in Directives
- 


# Forms

# Custom Directives

# Services

## Reference:
- [Download Angular](http://angularjs.org)


## Research:
- BehaviorDriven Development?
- Test Driven Development?
