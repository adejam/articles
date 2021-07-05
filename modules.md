# MODULES

JavaScript modules are reusable pieces of code that can be exported from one program and imported for use in another program.

Modules are particularly useful for a number of reasons. By separating code with similar logic into files called modules, i can:

- find, fix, and debug code more easily;

- reuse and recycle defined logic in different parts of our application;

- keep information private and protected from other modules;

- and, importantly, prevent pollution of the global namespace and potential naming collisions, by cautiously selecting variables and behavior loaded into a program.

There are two ways to implement modules in JavaScript: [Node.js’s](https://nodejs.org/en/about/) ```module.exports``` and ```require()``` syntax, as well as the ES6 ```import/export``` syntax.



## ```module.exports```

I can get started with modules by defining a module in one file and making the module available for use in another file with Node.js ```module.exports``` syntax. Every JavaScript file run in Node has a local ```module``` object with an ```exports``` property used to define what should be exported from the file.

Below is an example of how to define a module and how to export it using the statement ```module.exports```.

Creating a menu.js file i write:

```
let Menu = {};
Menu.specialty = "Roasted Beet Burger with Mint Sauce";

module.exports = Menu;
```

Considering what this code means.

1. ```let Menu = {};``` creates the object that represents the module ```Menu```. The statement contains an uppercase variable named ```Menu``` which is set equal to an empty object.

2. ```Menu.specialty``` is defined as a property of the Menu module. We add data to the Menu object by setting properties on that object and giving the properties a value.

3. ```"Roasted Beet Burger with Mint Sauce";``` is the value stored in the ```Menu.specialty``` property.

4. ```module.exports = Menu;``` exports the ```Menu``` object as a module. ```module``` is a variable that represents the module, and ```exports``` exposes the module as an object.

The pattern used to export modules is thus:

1. Create an object to represent the module.

2. Add properties or methods to the module object.

3. Export the module with ```module.exports```.


## ```require()```

To make use of the exported module and the behavior i define within it, i import the module into another file. the ```require()``` function is used to import modules.

For instance, say i want the module to control the menu’s data and behavior, and i want a separate file to handle placing an order. I would create a separate file **order.js** and import the ```Menu``` module from **menu.js** to **order.js** using ```require()```. ```require()``` takes a file path argument pointing to the original module file.

In **order.js** i would write:

```
const Menu = require('./menu.js');

function placeOrder() {
  console.log('My order is: ' + Menu.specialty);
}

placeOrder();
```

I now have the entire behavior of ```Menu``` available in **order.js**. It is noticeable that:

1. In ```order.js``` i import the module by creating a ```const``` variable called ```Menu``` and setting it equal to the value of the ```require()``` function. I can set the name of this variable to anything i like, such as ```menuItems```.

2. ```require()``` is a JavaScript function that loads a module. It’s argument is the file path of the module: ```./menu.js```. With ```require()```, the ```.js``` extension is optional and will be assumed if it is not included.

3. The ```placeOrder()``` function then uses the ```Menu``` module. By calling ```Menu.specialty```, i access the property specialty defined in the Menu module.

Taking a closer look, the pattern to import a module is:

1. Import the module with ```require()``` and assign it to a local variable.

2.Use the module and its properties within a program.


## More on ```module.exports```

I can also wrap any collection of data and functions in an object, and export the object using ```module.exports```. In ```menu.js```, i could write:

```
module.exports = {
  specialty: "Roasted Beet Burger with Mint Sauce",
  getSpecialty: function() {
    return this.specialty;
  }
};
```

In the above code, it is noticeable that:

1. ```module.exports``` exposes the current module as an object.

2. ```specialty``` and ```getSpecialty``` are properties on the object.

Then in **order.js**, i write:

```
const Menu = require('./menu.js');

console.log(Menu.getSpecialty());
```

Here i can still access the behavior in the ```Menu``` module.


## Export default

Node.js supports ```require()```/```module.exports```, but as of ES6, JavaScript supports a new more readable and flexible syntax for exporting modules. These are usually broken down into one of two techniques, default export and named exports.

We’ll begin with the first syntax, default export. The default export syntax works similarly to the ```module.exports``` syntax, allowing exportation of one module per file.

Taking a look at an example in menu.js.
```
let Menu = {};

export default Menu;
```

1. ```export default``` uses the JavaScript export statement to export JavaScript objects, functions, and primitive data types.

2. ```Menu``` refers to the name of the ```Menu``` object, the object that i am setting the properties on within the modules.

When using ES6 syntax, i use ```export default``` in place of ```module.exports```. Node.js doesn’t support ```export default``` by default, so ```module.exports``` is usually used for Node.js development and ES6 syntax is used for front-end development. As with most ES6 features, it is common to transpile code since ES6 is [not supported by all browsers](https://caniuse.com/#feat=es6).


## import

ES6 module syntax also introduces the ```import``` keyword for importing objects. In the **order.js** example, i import an object like this:

```
import Menu from './menu';
```

1. The import keyword begins the statement.

2. The keyword ```Menu``` here specifies the name of the variable to store the default export in.

3. ```from``` specifies where to load the module from.

4. ```'./menu'``` is the name of the module to load. When dealing with local files, it specifically refers to the name of the file without the extension of the file.

I can then continue using the ```Menu``` module in the **order.js** file.


## Named Exports

ES6 introduced a second common approach to export modules. In addition to export default, named exports allow exportation of data through the use of variables.

In menu.js i would be sure to give each piece of data a distinct variable name:

```
let specialty = '';
function isVegetarian() {
};
function isLowSodium() {
};

export { specialty, isVegetarian };
```

1. It is noticeable that, when i use named exports, i am not setting the properties on an object. Each export is stored in its own variable.

2. ```specialty``` is a string object, while ```isVegetarian``` and ```isLowSodium``` are objects in the form of functions. Recall that in JavaScript, every function is in fact a function object.

3. ```export { specialty, isVegetarian };``` exports objects by their variable names. Notice the keyword export is the prefix.

4. ```specialty``` and ```isVegetarian``` are exported, while ```isLowSodium``` is not exported, since it is not specified in the export syntax.


# Named Imports

To import objects stored in a variable, i use the ```import``` keyword and include the variables in a set of ```{}```.

In the **order.js** file, for example, i would write:

```
import { specialty, isVegetarian } from './menu';

console.log(specialty);
```


1. Here ```specialty``` and ```isVegetarian``` are imported.

2. If i did not want to import either of these variables, i could omit them from the import statement.

3. I can then use these objects as in within the code. For example, i would use ```specialty``` instead of ```Menu.specialty```.


## Export Named Exports

Named exports are also distinct in that they can be exported as soon as they are declared, by placing the keyword ```export``` in front of variable declarations.

In menu.js

```
export let specialty = '';
export function isVegetarian() {
};
function isLowSodium() {
};
```

1. The ```export``` keyword allows exporting objects upon declaration, as shown in ```export let specialty``` and ```export function isVegetarian() {}```.
2. I no longer need an ```export``` statement at the bottom of our file, since this behavior is handled above.


## Import Named Imports

To import variables that are declared, i simply have to use the original syntax that describes the variable name. In other words, exporting upon declaration does not have an impact on how i import the variables.

```
import { specialty, isVegetarian } from 'menu';
```

## Export as

Named exports also conveniently offer a way to change the name of variables when i export or import them. I can do this with the ```as``` keyword.

Seeing how this works. In our **menu.js** example

```
let specialty = '';
let isVegetarian = function() {
};
let isLowSodium = function() {
};

export { specialty as chefsSpecial, isVegetarian as isVeg, isLowSodium };
```

In the above example, take a look at the ```export``` statement at the bottom of the of the file.

1. The ```as``` keyword allows us to give a variable name an alias as demonstrated in ```specialty as chefsSpecial``` and ```isVegetarian as isVeg```.

2. Since i did not give ```isLowSodium``` an alias, it will maintain its original name.


## Import as


To import named export aliases with the ```as``` keyword, i add the aliased variable in our import statement.

```
import { chefsSpecial, isVeg } from './menu';
```

In **orders.js**

1. I import ```chefsSpecial``` and ```isVeg``` from the ```Menu``` object.

2. Here, it is noticeable that i have an option to alias an object that was not previously aliased when exported. For example, the ```isLowSodium``` object that i exported could be aliased with the ```as``` keyword when imported: ```import {isLowSodium as saltFree} from 'Menu';```

Another way of using aliases is to import the entire module as an alias:

```
import * as Carte from './menu';

Carte.chefsSpecial;
Carte.isVeg();
Carte.isLowSodium();
```

1. This allows importing an entire module from **menu.js** as an alias ```Carte```.

2. In this example, whatever name i exported would be available as properties of that module. For example, if i exported the aliases ```chefsSpecial``` and ```isVeg```, these would be available to us. If i did not give an alias to ```isLowSodium```, i would call it as defined on the ```Carte``` module.


## Combining Export Statements

I can also use named exports and default exports together. In **menu.js**:

```
let specialty = '';
function isVegetarian() {
};
function isLowSodium() {
};
function isGlutenFree() {
};

export { specialty as chefsSpecial, isVegetarian as isVeg };
export default isGlutenFree;
```

Here i use the keyword ```export``` to export the named exports at the bottom of the file. Meanwhile, i export the ```isGlutenFree``` variable using the ```export default``` syntax.

This would also work if i exported most of the variables as declared and exported others with the ```export default``` syntax.

```
export let Menu = {};

export let specialty = '';
export let isVegetarian = function() {
};
export let isLowSodium = function() {
};
let isGlutenFree = function() {
};

export default isGlutenFree;
```

Here i use the export keyword to export the variables upon declaration, and again export the ```isGlutenFree``` variable using the ```export default``` syntax

While it’s better to avoid combining two methods of exporting, it is useful on occasion. For example, if one suspect developers may only be interested in importing a specific function and won’t need to import the entire default export.


## Combining Import Statements

I can import the collection of objects and functions with the same data.

I can use an ```import``` keyword to import both types of variables as such:

```
import { specialty, isVegetarian, isLowSodium } from './menu';

import GlutenFree from './menu';
```