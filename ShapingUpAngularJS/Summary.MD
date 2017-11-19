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
- **Filters** are ways to control the look of output.
- The **Currency Filter** will convert numbers into a currency format.
- `{{product.price | currency}}`
- The formula is `{{ data | filter:options}}`.
```angularjs
{{'1388123412323' | date:'MM/dd/yyy @ h:mma'}}
```
- There is also `limitTo:<n>`.
- This can also be passed inside angular expressions; to limit the number of loops.
- You can also `orderBy:'-price'` to order them by an attribute.
- Since an img tag tries to before the angular code, you will need to include `ng-src` to tell it to wait.
- We can tell angular not to enact this function unless it is clicked using `ng-click="tab = 1"`.
- Then, we can have it be printed by just using `{{tab}}`.
- Expressions like this are a two way data binding.
- You can mark a div using `ng-show="tab == 1"` to define that tab as the *1* tab.
- You can specify which *tab* to show up first using `ng-init="tab = 1"`.
- You can tell Angular which is active using `ng-class="{active:tab === 1}"`.
- But, we shouldn't be including all this logic in the webpage so create a new controller.
```js
app.controller('TabController', function(){
    this.tab = 1;

    this.setTab = function( selectedTab ){
      this.tab = selectedTab;
    };

    this.isSet = function( selectedTab ){
      return this.tab == selectedTab;
    };
  });
```

# Forms
- `ng-model` binds the form element value to the property.
- For example `ng-model="review.author"`.
- You can have angular submit with `ng-submit="reviewCtrl.addReview(product)"`.
- To use angular validation, you're going to want to turn off html validations.
- Do this to include `novalidate` at the end of the form declaration.
- We can also add what fields are required by adding `required` at the end of each inputs declaration.
- You can debug a form using `{{<formName>.$valid}}`.
- This also checks to see if an email address is valid.
- You could include this in the `ng-submit` expression to prevent it from submiting without valid info.
- Under the hood, Angular marks fields not touched yet with `ng-pristine ng-valid` but removes them once clicked.
- You can create some CSS to simply highlight the field when the `ng-invalid` class exists.

# Custom Directives
- Angular also supports snippets; I think of them as templates.
- You then use `ng-include="'product-title.html'"`.
- Don't overlook that there are double and single quotes here.
- **Directives** allow you to write HTMLthat expresses the behavior of your application.
- There are a few kinds of Custom Directives:
 * Template-expanding Directives: define a custom tag or attribute to expand or replace.
 * Expressing complex UI
 * Calling events to event handlers
 * Reusing common components
- You define a directive using:
```js
app.directive('productTitle', function(){
  return {
    restrict: 'E' //type of directive
    templateUrl: 'product-title.html'
  };
});
```
- Some browsers don't like self closing tags with custom elements.
- The Attribute Directive uses `A` instead of `E`.
- Angular allows you to write expressive HTML through Directives.
- Don't forget to turn the `div` into the `<product-description>` instead.
- The Attribute Directive, based on its name, does not need to change the `div`.
- You can insert the controller into the directive using the `controller:` keyword.
- You need to also declare what the name of the controller will be using `controllerAs: 'panels'`.

# Services
- To better manage all this code, it's better to create a new module.
- Now, make sure to update the *store* module to tell it that it depends on `store-products` module.
- You're also want to include the new *products.js* file to the website.
- Services extend the controller functionality.
- Such as:
  * Fetching JSON data
  * Logging
  * Filtering
- All services start with a `$`.
- `$http({method: 'GET', url: '/products.json'})` to use http and access the data.
- Or, `$http.get( {'products.json', {apiKey: 'myApiKey' }})`.
- Promises tell you about the status of a request.
- Now we need to tell the Controller that we need the service.
- Formula: `app.controller('SomeController', [ '$http', '$log', function( $http, $log){}])`.
```js
app.controller('StoreController', ['$http', function($http){
    var store = this;
    store.products = [];

    $http.get('/store-products.json').success(function(data){
        store.products = data;
    });
  }]);
```


## Reference:
- [Download Angular](http://angularjs.org)

## Research:
- BehaviorDriven Development?
- Test Driven Development?
- [plnkr](http://plnkr.co) ?
