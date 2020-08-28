# OBJECTS

In JavaScript, almost "everything" is an object. JavaScript objects are containers storing related data and functionality.
There are only seven fundamental data types in JavaScript, and six of those are the primitive data types: string, number, boolean, null, undefined, and symbol. With the seventh type, objects, the code is opened to more complex possibilities. JavaScript objects can be used to model real-world things, like a phone ehich have properties like color, size, model which in turn have individual values like black, 6', andriod 5.4, or objects can be used to build the data structures that make the web possible.

## Creating Object Literals

Objects can be assigned to variables just like any JavaScript type. Curly braces `{}` are used, to designate an *object literal*:

```
let spaceship = {}; // spaceship is an empty object
```

Objects data are organized into *key-value pairs* which are unordered. A key is like a variable name that points to a location in memory that holds a value.

![key_value](/images/key_value.svg)

A key’s value can be of any data type in the language including functions or other objects.

A key-value pair is made by writing the key’s name, or *identifier*, followed by a colon and then the value. Each key-value pair in an object literal is seperated with a comma (```,```). Keys are strings, but when there is a key that does not have any special characters in it, JavaScript allows omitting the quotation marks:

![object literal diagram](/images/objectliteraldiagram.svg)

```
// An object literal with two key-value pairs
let spaceship = {
  'Fuel Type': 'diesel',
  color: 'silver'
};
```

The ```spaceship``` object has two properties ```Fuel Type``` and ```color```. ```'Fuel Type'``` has quotation marks because it contains a space character.


## Accessing Properties

There are two ways to access an object’s property.

### dot ```.``` notation.

I have previously used dot notation to access the properties and methods of built-in objects and data instances:

```
'hello'.length; // Returns 5
```

With property dot notation, i write the object’s name, followed by the dot operator and then the property name (key):

```
let spaceship = {
  homePlanet: 'Earth',
  color: 'silver'
};
spaceship.homePlanet; // Returns 'Earth',
spaceship.color; // Returns 'silver',
```

![object_dot_notation](/images/object_dot_notation.svg)

If i try to access a property that does not exist on that object, ```undefined``` will be returned.

```
spaceship.favoriteIcecream; // Returns undefined
```


### Bracket Notation

The second way to access a key’s value is by using bracket notation, ```[ ]```.

I have previously used bracket notation when indexing an array:

```
['A', 'B', 'C'][0]; // Returns 'A'
```

To use bracket notation to access an object’s property, i pass in the property name (key) as a string.


![object_access_bracket](/images/object_access_bracket.svg)

 Bracket notation **must** be used when accessing keys that have numbers, spaces, or special characters in them. Without bracket notation in these situations, the code would throw an error.

```
let spaceship = {
  'Fuel Type': 'Turbo Fuel',
  'Active Duty': true,
  homePlanet: 'Earth',
  numCrew: 5
};
spaceship['Active Duty'];   // Returns true
spaceship['Fuel Type'];   // Returns  'Turbo Fuel'
spaceship['numCrew'];   // Returns 5
spaceship['!!!!!!!!!!!!!!!'];   // Returns undefined
```

With bracket notation i can also use a variable inside the brackets to select the keys of an object. This can be especially helpful when working with functions:

```
let returnAnyProp = (objectName, propName) => objectName[propName];

returnAnyProp(spaceship, 'homePlanet'); // Returns 'Earth'
```

If i tried to write the ```returnAnyProp()``` function with dot notation (```objectName.propName```) the computer would look for a key of ```'propName'``` on the object and not the value of the ```propName``` parameter.


## Property Assignment

Once an object is defined, its properties are mutable meaning the properties can be updated after creating them!

I can use either dot notation, ```.```, or bracket notation, ```[]```, and the assignment operator, ```=``` to add new key-value pairs to an object or change an existing property.


![object_update_property](/images/object_update_property.svg)

One of two things can happen with property assignment:

- If the property already exists on the object, whatever value it held before will be replaced with the newly assigned value.

- If there was no property with that name, a new property will be added to the object.

It’s important to know that although an object declared with const can't be reassigned, it can still be mutated, meaning i can add new properties and change the properties that are there.

```
const spaceship = {type: 'shuttle'};
spaceship = {type: 'alien'}; // TypeError: Assignment to constant variable.
spaceship.type = 'alien'; // Changes the value of the type property
spaceship.speed = 'Mach 5'; // Creates a new key of 'speed' with a value of 'Mach 5'
```

I can delete a property from an object with the delete operator.

```
const spaceship = {
  'Fuel Type': 'Turbo Fuel',
  homePlanet: 'Earth',
  mission: 'Explore the universe'
};

delete spaceship.mission;  // Removes the mission property
```

## Methods


When the data stored on an object is a function it is called a *method*. A **property** is what an object has, while a **method** is what an object does.

Object methods are familiar because i’ve been using them all along! For example ```console``` is a global javascript object and ```.log()``` is a method on that object. ```Math``` is also a global javascript object and ```.floor()``` is a method on it.

I can include methods in the object literals by creating ordinary, comma-separated key-value pairs. The key serves as the method’s name, while the value is an anonymous function expression.

```
const aboutMe = {
  about: function () {
    console.log('Hello! I am Adeleye Oluwaloseyi Jamiu.I am a programmer')
  }
};
```

With the new method syntax introduced in ES6 i can omit the colon and the function keyword.

```
const aboutMe = {
  about () {
    console.log('I am Adeleye Oluwaloseyi Jamiu.I am a programmer')
  }
};
```

Object methods are invoked by appending the object’s name with the dot operator followed by the method name and parentheses:

```
aboutMe.about(); // Prints 'I am Adeleye Oluwaloseyi Jamiu.I am a programmer'
```


## Nested Objects


In application code, objects are often nested— an object might have another object as a property which in turn could have a property that’s an array of even more objects!

In the ```spaceship``` object, i want a ```crew``` object. This will contain all the crew members who do important work on the craft. Each of those ```crew``` members are objects themselves. They have properties like ```name```, and ```degree```, and they each have unique methods based on their roles. I can also nest other objects in the ```spaceship``` such as a ```telescope``` or nest details about the spaceship’s computers inside a parent ```nanoelectronics``` object.


```
const spaceship = {
     telescope: {
        yearBuilt: 2018,
        model: '91031-XLT',
        focalLength: 2032
     },
    crew: {
        captain: {
            name: 'Sandra',
            degree: 'Computer Engineering',
            encourageTeam() { console.log('We got this!') }
         }
    },
    engine: {
        model: 'Nimbus2000'
     },
     nanoelectronics: {
         computer: {
            terabytes: 100,
            monitors: 'HD'
         },
        'back-up': {
           battery: 'Lithium',
           terabytes: 50
         }
    }
};
```

I can chain operators to access nested properties. I'll have to pay attention to which operator makes sense to use in each layer. It can be helpful to pretend i am the computer and evaluate each expression from left to right so that each operation starts to feel a little more manageable.

```
spaceship.nanoelectronics['back-up'].battery; // Returns 'Lithium'
```

In the preceding code:

- First the computer evaluates ```spaceship.nanoelectronics```, which results in an object containing the ```back-up``` and computer objects.

- We accessed the ```back-up``` object by appending ```['back-up']```.

- The ```back-up``` object has a ```battery``` property, accessed with ```.battery``` which returned the value stored there: ```'Lithium'```.


## Pass By Reference

Objects are *passed by reference*. This means when a variable assigned to an object is passed into a function as an argument, the computer interprets the parameter name as pointing to the space in memory holding that object. As a result, functions which change object properties actually mutate the object permanently (even when the object is assigned to a ```const``` variable).

```
const spaceship = {
  homePlanet : 'Earth',
  color : 'silver'
};

let paintIt = obj => {
  obj.color = 'glorious gold'
};

paintIt(spaceship);

spaceship.color // Returns 'glorious gold'
```

Our function ```paintIt()``` permanently changed the color of our ```spaceship``` object. However, reassignment of the ```spaceship``` variable wouldn’t work in the same way:

```
let spaceship = {
  homePlanet : 'Earth',
  color : 'red'
};
let tryReassignment = obj => {
  obj = {
    identified : false,
    'transport type' : 'flying'
  }
  console.log(obj) // Prints {'identified': false, 'transport type': 'flying'}

};
tryReassignment(spaceship) // The attempt at reassignment does not work.
spaceship // Still returns {homePlanet : 'Earth', color : 'red'};

spaceship = {
  identified : false,
  'transport type': 'flying'
}; // Regular reassignment still works.

```

Looking at what happened in the code example:

- I declared this ```spaceship``` object with ```let```. This allowed us to reassign it to a new object with ```identified``` and ```'transport type'``` properties with no problems.

- When i tried the same thing using a function designed to reassign the object passed into it, the reassignment didn’t stick (even though calling ```console.log()``` on the object produced the expected result).

- When i passed ```spaceship``` into that function, ```obj``` became a reference to the memory location of the ```spaceship``` object, but not to the ```spaceship``` variable. This is because the ```obj``` parameter of the ```tryReassignment()``` function is a variable in its own right. The body of ```tryReassignment()``` has no knowledge of the ```spaceship``` variable at all!

- When i did the reassignment in the body of ```tryReassignment()```, the ```obj``` variable came to refer to the memory location of the object ```{'identified' : false, 'transport type' : 'flying'}```, while the ```spaceship``` variable was completely unchanged from its earlier value.


## Looping Through Objects

Loops are programming tools that repeat a block of code until a condition is met. We iterate through arrays using their numerical indexing, but the key-value pairs in objects aren’t ordered! [JavaScript has given an alternative solution for iterating through objects with the ```for...in``` syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...in).

```for...in``` will execute a given block of code for each property in an object.

```
let spaceship = {
    crew: {
    captain: {
        name: 'Lily',
        degree: 'Computer Engineering',
        cheerTeam() { console.log('You got this!') }
        },
    'chief officer': {
        name: 'Dan',
        degree: 'Aerospace Engineering',
        agree() { console.log('I agree, captain!') }
        },
    medic: {
        name: 'Clementine',
        degree: 'Physics',
        announce() { console.log(`Jets on!`) } },
    translator: {
        name: 'Shauna',
        degree: 'Conservation Science',
        powerFuel() { console.log('The tank is full!') }
        }
    }
};
// for...in
for (let crewMember in spaceship.crew) {
  console.log(`${crewMember}: ${spaceship.crew[crewMember].name}`)
};

/*Outputs:
captain: Lily
chief officer: Dan
medic: Clementine
translator: Shauna
*/
```

The ```for...in``` will iterate through each element of the ```spaceship.crew``` object. In each iteration, the variable ```crewMember``` is set to one of ```spaceship.crew```‘s keys, enabling logging a list of crew members’ role and ```name```.


## The ```this``` Keyword

Objects are collections of related data and functionality. That functionality is stored in methods on the objects:

```
const goat = {
  dietType: 'herbivore',
  makeSound() {
    console.log('baaa');
  }
};
```

In the goat object i have a ```.makeSound()``` method. The ```.makeSound()``` method can be invoked on ```goat```.

```
goat.makeSound(); // Prints baaa
```

I have a ```goat``` object that can print ```baaa``` to the console. If i wanted to add a new method to the ```goat``` object called ```.diet()``` that prints the ```goat```‘s ```dietType```?


```
const goat = {
  dietType: 'herbivore',
  makeSound() {
    console.log('baaa');
  },
  diet() {
    console.log(dietType);
  }
};
goat.diet();
// Output will be "ReferenceError: dietType is not defined"
```

```dietType``` is not defined even though it’s a property of ```goat``` because inside the scope of the ```.diet()``` method, i don’t automatically have access to other properties of the ```goat``` object.

Here’s where the ```this``` keyword comes to the rescue. If i change the ```.diet()``` method to use the ```this```, the ```.diet()``` works! :

```
const goat = {
  dietType: 'herbivore',
  makeSound() {
    console.log('baaa');
  },
  diet() {
    console.log(this.dietType);
  }
};

goat.diet();
// Output: herbivore
```

The ```this``` keyword references the *calling* object which provides access to the calling object’s properties. In the example above, the calling object is ```goat``` and by using ```this``` i am accessing the ```goat``` object itself, and then the ```dietType``` property of ```goat``` by using property dot notation.


## Arrow Functions and this


For a method, the calling object is the object the method belongs to. If i use the ```this``` keyword in a method then the value of ```this``` is the calling object. However, it becomes a bit more complicated when  using arrow functions for methods. Take a look at the example below:

```
const goat = {
  dietType: 'herbivore',
  makeSound() {
    console.log('baaa');
  },
  diet: () => {
    console.log(this.dietType);
  }
};

goat.diet(); // Prints undefined
```

```goat.diet()``` log ```undefined``` as the ```.diet()``` is defined using an arrow function.

Arrow functions inherently *bind*, or tie, an already defined ```this``` value to the function itself that is NOT the calling object. In the code snippet above, the value of ```this``` is the *global object*, or an object that exists in the global scope, which doesn’t have a ```dietType``` property and therefore returns ```undefined```.

To read more about either arrow functions or the global object check out the MDN documentation of the [
global object](https://developer.mozilla.org/en-US/docs/Glossary/Global_object) and [arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions).

The key takeaway from the example above is to **avoid** using arrow functions when using ```this``` in a method!


## Privacy

Accessing and updating properties is fundamental in working with objects. However, there are cases in which i don’t want other code simply accessing and updating an object’s properties. When discussing privacy in objects, i define it as the idea that only certain properties should be mutable or able to change in value.

Certain languages have privacy built-in for objects, but JavaScript does not have this feature. Rather, JavaScript developers follow naming conventions that signal to other developers how to interact with a property. One common convention is to place an underscore _ before the name of a property to mean that the property should not be altered. Here’s an example of using _ to prepend a property.

```
const bankAccount = {
  _amount: 1000
}
```

In the example above, the ```_amount``` is not intended to be directly manipulated.

Even so, it is still possible to reassign ```_amount```:

```
bankAccount._amount = 1000000;
```

The use of methods called *getters* and *setters* are used to respect the intention of properties prepended, or began, with ```_```. *Getters* can return the value of internal properties and *setters* can safely reassign property values.



## Getters

```Getters``` are methods that get and return the internal properties of an object. But they can do more than just retrieve the value of a property! Taking a look at a getter method:

```
const person = {
  _firstName: 'John',
  _lastName: 'Doe',
  get fullName() {
    if (this._firstName && this._lastName){
      return `${this._firstName} ${this._lastName}`;
    } else {
      return 'Missing a first name or a last name.';
    }
  }
}

// To call the getter method:
person.fullName; // 'John Doe'
```

It is noticeable that in the getter method above:

- I use the ```get``` keyword followed by a function.

- I use an ```if...else``` conditional to check if both ```_firstName``` and ```_lastName``` exist (by making sure they both return truthy values) and then ```return``` a different value depending on the result.

- I can access the calling object’s internal properties using this. In ```fullName```, i am accessing both ```this._firstName``` and ```this._lastName```.

- In the last line i called ```fullName``` on ```person```. In general, getter methods do not need to be called with a set of parentheses. Syntactically, it looks like a property is being accessed.

Some notable advantages of using getter methods:

- Getters can perform an action on the data when getting a property.

- Getters can return different values using conditionals.

- In a getter, the properties of the calling object can be accessed using ```this```.

- The functionality of the code is easier for other developers to understand.

Another thing to keep in mind when using getter (and setter) methods is that properties cannot share the same name as the getter/setter function. If that happens, then calling the method will result in an infinite call stack error. One workaround is to add an underscore before the property name like i did in the example above.


## Setters

Along with getter methods, i can also create ```setter``` methods which reassign values of existing properties within an object.

```
const person = {
  _age: 37,
  set age(newAge){
    if (typeof newAge === 'number'){
      this._age = newAge;
    } else {
      console.log('You must assign a number to age');
    }
  }
};
```

In the example above:

- I can perform a check for what value is being assigned to ```this._age```.

- When i use the setter method, only values that are numbers will reassign ```this._age```.

- There are different outputs depending on what values are used to reassign ```this._age```.

Then to use the setter method:

```
person.age = 40;
console.log(person._age); // Logs: 40
person.age = '40'; // Logs: You must assign a number to age
```

Setter methods like ```age``` do not need to be called with a set of parentheses. Syntactically, it looks like i am reassigning the value of a property.

Like getter methods, there are similar advantages to using setter methods that include checking input, performing actions on properties, and displaying a clear intention for how the object is supposed to be used. Nonetheless, even with a setter method, it is still possible to directly reassign properties. For example, in the example above, i can still set ```._age``` directly:

```
person._age = 'forty-five'
console.log(person._age); // Prints forty-five
```

## Factory Functions

So far i've been creating objects individually, but there are times where i want to create many instances of an object quickly. Here’s where factory functions come in. A real world factory manufactures multiple copies of an item quickly and on a massive scale. A factory function is a function that returns an object and can be reused to make multiple object instances. Factory functions can also have parameters allowing us to customize the object that gets returned.

Let’s say i wanted to create an object to represent monsters in JavaScript. There are many different types of monsters and i could go about making each monster individually but i can also use a factory function to make it easier. To achieve this diabolical plan of creating multiple monsters objects, i can use a factory function that has parameters:

```
const monsterFactory = (name, age, energySource, catchPhrase) => {
  return {
    name: name,
    age: age,
    energySource: energySource,
    scare() {
      console.log(catchPhrase);
    }
  }
};

```


In the ```monsterFactory``` function above, it has four parameters and returns an object that has the properties: ```name```, ```age```, ```energySource```, and ```scare()```. To make an object that represents a specific monster like a ghost, i can call ```monsterFactory``` with the necessary arguments and assign the return value to a variable:

```
const ghost = monsterFactory('Ghouly', 251, 'ectoplasm', 'BOO!');
ghost.scare(); // 'BOO!'
```

Now i have a ghost object as a result of calling monsterFactory() with the needed arguments. With ```monsterFactory``` in place, i don’t have to create an object literal every time i need a new monster. Instead, i can invoke the ```monsterFactory``` function with the necessary arguments.



## Property Value Shorthand


ES6 introduced some new shortcuts for assigning properties to variables known as *destructuring*.

In the previous exercise, i created a factory function that helped create objects. I had to assign each property a key and value even though the key name was the same as the parameter name i assigned to it. Below is a truncated version of the factory function:

```
const monsterFactory = (name, age) => {
  return {
    name: name,
    age: age
  }
};
```

Imagine if i had to include more properties, that process would quickly become tedious! But i can use a destructuring technique, called *property value shorthand*, to save myself some keystrokes. The example below works exactly like the example above:

```
const monsterFactory = (name, age) => {
  return {
    name,
    age
  }
};
```


## Destructured Assignment


I often want to extract key-value pairs from objects and save them as variables. Take for example the following object:

```
const vampire = {
  name: 'Dracula',
  residence: 'Transylvania',
  preferences: {
    day: 'stay inside',
    night: 'satisfy appetite'
  }
};

```

If i wanted to extract the ```residence``` property as a variable, i could use the following code:

```
const residence = vampire.residence;
console.log(residence); // Prints 'Transylvania'
```

However, i can also take advantage of a destructuring technique called ```destructured assignment``` to save ourselves some keystrokes. In destructured assignment i create a variable with the name of an object’s key that is wrapped in curly braces ```{ }``` and assign to it the object. Taking a look at the example below:

```
const { residence } = vampire;
console.log(residence); // Prints 'Transylvania'
```

Look back at the ```vampire``` object’s properties in the first code example. Then, in the example above, i declare a new variable ```residence``` that extracts the value of the ```residence``` property of ```vampire```. When i log the value of residence to the console, ```'Transylvania'``` is printed.

I can even use destructured assignment to grab nested properties of an object:

```
const { day } = vampire.preferences;
console.log(day); // Prints 'stay inside'
```

## Built-in Object Methods

In the previous exercises i've been creating instances of objects that have their own methods. But, i can also take advantage of built-in methods for Objects!

For example, i have access to object instance methods like: ```.hasOwnProperty()```, ```.valueOf()```, and many more at [MDN’s object instance documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object#Methods).

There are also useful Object class methods such as ```Object.assign()```, ```Object.entries()```, and ```Object.keys()``` just to name a few. For a comprehensive list, browse: [MDN’s object instance documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object#Methods_of_the_Object_constructor).

