# OBJECTS

In JavaScript, almost "everything" is an object. Many components of the language are actually objects under the hood, and even the parts that aren’t— like strings or numbers— can still act like objects in some instances.
There are only seven fundamental data types in JavaScript, and six of those are the primitive data types: string, number, boolean, null, undefined, and symbol. With the seventh type, objects, the code is opened to more complex possibilities. JavaScript objects can be used to model real-world things, like a basketball, or objects can be used to build the data structures that make the web possible.

At their core, JavaScript objects are containers storing related data and functionality, but that deceptively simple task is extremely powerful in practice.



## Creating Object Literals

Objects can be assigned to variables just like any JavaScript type. Curly braces ```{}``` are used, to designate an *object literal*:

```
let spaceship = {}; // spaceship is an empty object
```

An object is filled with unordered data. This data is organized into *key-value pairs*. A key is like a variable name that points to a location in memory that holds a value.

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