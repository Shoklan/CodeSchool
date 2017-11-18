# Try Ember
## Nathaniel Bibler

# Getting Started
- Must know HTML and JS.
- It's built on node.js .
- Ember is an Open Source MVC Framework for creating ambitious web applications.
- Ember was actually built out of Apple's SproutCore.
- **MVC** stands for *Model-View-Controller*.
- The official way to create an Ember app is via the *Ember CLI*.
- This is installed throught *npm* and node.
- You can install Ember using `npm install -g ember-cli`.
- Running `ember version` will tell you the version installed.
- To create a project use `ember new <project_name> <options>`.
- You can run a development server using `ember serve`.

# Routing and Templating
- A **Template** instructs ember on what to render for the user's request.
- Ember uses the **handlebars** templating library.
- The *.hbs* file extention is what *handlebars* uses.
- Any changes you make are automatically pushed to the users.
- A **Handle Expression**, denoted by `{{}}` means that we're going to be inserting values here.
- If we create a *app/templates/index.hbs* then it will be loaded instead of blank.
- The **router** manages the application's state and maps it to the proper URL.
- We configure the *routes* in the *router.js* file.
- Route format:
```
Router.map( function(){
    this.route( 'orders', {path: '/orders' });
});
```
- Ember can infer the path if the name path are the same.
- Tfr. the path parameter can be ignored.
- You can use normal links but then you lose the speed advantage.
- Instead, we use the **Link-To Helper**: `{{#link-to "orders"}}orders{{/link-to}}`
- If you need to add other classes, then you just pass `class="other-classes listed-here"`.
- This can also be extended to the type of html element.
- `tagName="div"` will render it as a div element.
- There are tons more Helpers too.
- Ember changes the url because that's how it monitors the state.
- It's also a valid url for your site and can be a bookmark.
- The router accepts the request but doesn't care about the template.
- The template is what is rendered but nothing is telling it what data to render.
- The router does not talk directly  to the template.
- **Routes** sit between the router and the Template.
- To create a new route use `ember generate route <route_name>`.
- This creates a file in *app/routes* called *orders.js*.
- You can extend this route by modifying the `export default Ember.Route.extend({});`.
- One way to modify this is to add a model function; or, a **Hook**.
- **Model*** represents the data and what is made available to its templates.
- The model is a JSON object and is refered to as *model.id* to access the id attribute.
- If the model is an array, you can use the **Each Helper**
```
{{#each model as |order|}}
  Order {{order.id}} for {{order.name}}<br />
{{/each}}
```
- There are tons of other **Route Hooks**.
- To navigate to a single item, we need a new state.
- `this.route( 'order', {path: '/orders/:order_id'});`
- The `:order_id` is called a **Dynamic Segment**.
- It instructs the router to match anything thats at that location in the url.
- To get the *hook* to accept *dynamic segments* you just need to pass `params` to the model in the *routes.js*.
- in the template file, you pass `{{#link-to "order" order}}`.
- To solve the loss of data, you use **Nested Routes**.
- This allows for multiple templates to be displayed on the page simultaniously.
- To do this, you:
  1. add `function()` with the routes inside it.
  2. This makes all the paths children of the *orders* route.
- Due to this change, you need to adjust the template to:
```
{{#each model as |order|}}
  {{#link-to "orders.order" order}}
    Order {{order.id}} for {{order.name}}<br />
  {{/link-to}}
{{/each}}

{{outlet}}
```
- You still need the outlet at the bottom.
- Further, you'll want to now create an orders subdirectory in routes and templates.
- Remember the model needs an explicit return statement.
- *Routes* are the *model* part.
- Routes only pass the model to each page.

# Models and services
- 



# Actions

# Properties and Components
