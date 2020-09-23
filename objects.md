# LEARNING JAVASCRIPT SERIES: JAVASCRIPT OBJECTS SERIES 1

This objective of this article is to Explain:

- How to create object literals in javascript.
- Accessing objects using the dot `.` notation and bracket `[]` notation.
- Property assignments.
- Object methods.
- Nested objects.

In JavaScript, almost "everything" is an object. JavaScript objects are containers storing related data and functionality.
JavaScript objects can be used to model real-world things, like a phone which have properties like color, size, model which in turn have individual values like black, 6', Andriod 5.4, or objects can be used to build the data structures that make the web possible.

## Using `new` keyword to create an object

In javascript we can use the `new` keyword to create an object like below:

```js
var aboutMe = new Object();
aboutMe.firstName = "Adeleye";
aboutMe.lastName = "Jamiu";
aboutMe.age = 50;
aboutMe.Programme = "javascript";
```

In the above example we created an object `aboutMe` using the `new` keyword. The `aboutMe` object is then assigned properties (`firstname`, `lastname`, `age`, `programme`) with their respective values.

This method however is not the best way of creating an object. 
For simplicity, readability and execution speed, The best method for creating an object is using **Object Literals**.

## Creating Object Literals

Objects can be assigned to variables just like any JavaScript type. Curly braces `{}` are used, to designate an _object literal_:

```js
let name = {}; // name is an empty object
```

Objects data are organized into _key-value pairs_ which are unordered. A key is like a variable name that points to a location in memory that holds a value.

A key’s value can be of any data type in the language including functions or other objects.

A key-value pair is made by writing the key’s name, or _identifier_, followed by a colon and then the value. Each key-value pair in an object literal is separated with a comma (`,`). Keys are strings, but when there is a key that does not have any special characters in it, JavaScript allows omitting the quotation marks:

```js
// An object literal with two key-value pairs
let name = {
  "First Name": "Jamiu",
  gender: "male",
};
```

The `name` object has two properties `"First Name"` and `gender`. `'First Name'` has quotation marks because it contains a space character.

## Accessing Properties

There are two ways to access an object’s property.

### dot `.` notation.

dot notation has been to access the properties and methods of built-in objects and data instances:

```js
"hello".length; // Returns 5
```

With property dot notation, we write the object’s name, followed by the dot operator and then the property name (key):

```js
let name = {
  firstname: "Jamiu",
  gender: "male",
};
name.firstname; // Returns 'Jamiu',
name.gender; // Returns 'male',
```

Accessing a property that does not exist on an object, returns `undefined`.

```js
name.age; // Returns undefined
```

### Bracket Notation

The second way to access a key’s value is by using bracket notation, `[ ]`.

Bracket notation are used when indexing an array:

```js
["A", "B", "C"][0]; // Returns 'A'
```

To use bracket notation to access an object’s property, we pass in the property name (key) as a string.

Bracket notation **must** be used when accessing keys that have numbers, spaces, or special characters in them. Without bracket notation in these situations, the code would throw an error.

```js
let name = {
  "First Name": "Jamiu",
  male: true,
  country: "Nigeria",
  age: 5,
};
name["male"]; // Returns true
name["First Name"]; // Returns  'Jamiu'
name["age"]; // Returns 5
name["!!!!!!!!!!!!!!!"]; // Returns undefined
```

With bracket notation we can also use a variable inside the brackets to select the keys of an object. This can be especially helpful when working with functions:

```js
let returnAnyProp = (objectName, propName) => objectName[propName];

returnAnyProp(name, "First Name"); // Returns 'Jamiu'
```

If we tried to write the `returnAnyProp()` function with dot notation (`objectName.propName`) the computer would look for a key of `'propName'` on the object and not the value of the `propName` parameter.

## Property Assignment

Once an object is defined, its properties are mutable meaning the properties can be updated after creating them!

we can use either dot notation, `.`, or bracket notation, `[]`, and the assignment operator, `=` to add new key-value pairs to an object or change an existing property.

One of two things can happen with property assignment:

- If the property already exists on the object, whatever value it held before will be replaced with the newly assigned value.

- If there was no property with that name, a new property will be added to the object.

It’s important to know that although an object declared with const can't be reassigned, it can still be mutated, meaning we can add new properties and change the properties that are there.

```js
const name = { firstname: "Jamiu" };
name = { firstname: "seyi" }; // TypeError: Assignment to constant variable.
name.firstname = "seyi"; // Changes the value of the firstname property
name.age = "5 years"; // Creates a new key of 'age' with a value of '5 years'
```

we can delete a property from an object with the delete operator.

```js
const vehicle = {
  "First Name": "Adeleye",
  gender: "male",
  about: "A programmer",
};

delete name.about; // Removes the about property
```

## Methods

A function can be stored on an object. This is called a _method_. A **property** is what an object has, while a **method** is what an object does.

For example `console` is a global javascript object and `.log` is a method on that object. `Math` is also a global javascript object and `.floor()` is a method on it.

we can include methods in the object literals by creating ordinary, comma-separated key-value pairs. The key serves as the method’s name, while the value is an anonymous function expression.

```js
const aboutMe = {
  about: function () {
    console.log("Hello! I am Adeleye Oluwaloseyi Jamiu.I am a programmer");
  },
};
```

The colon and the function keyword can be omitted with the new method syntax introduced in ES6.

```js
const aboutMe = {
  about() {
    console.log("I am Adeleye Oluwaloseyi Jamiu.I am a programmer");
  },
};
```

Object methods are invoked by appending the object’s name with the dot operator followed by the method name and parentheses:

```js
aboutMe.about(); // Prints 'I am Adeleye Oluwaloseyi Jamiu.I am a programmer'
```

## Nested Objects

Ojects are often nested— an object can have another object as a property which in turn could have a property that’s an array of even more objects!. Looking at the example below:

```js
const soccerClub = {
  structures: {
    stadium: 'Camp Nou',
    trainingGround: 'Johan Cryuff Stadium',
  },
  coaches: {
    headCoach: 'Guardiola',
    fitnessCoach: 'Klopp',
    nutritionCoach: 'Conte',
  }
  team: {
    mainTeam: {
      forwards: ['Messi', 'Dembele', 'Ansu Fati', 'Trincao', 'Griezmann'],
      midfielders: ['De jong', 'Busquets', 'Pjanic', 'Coutinho'],
      defenders: ['Pique', 'lenglet', 'Jordi Alba', 'Firpo'],
      goalkeppers: ['Ter stegen', 'Neto'],
    },
    'youth-team': {
      forwards: ['Pedri', 'Konrad'],
      midfielders: ['Riqui', 'alena'],
      defenders: ['sergio', 'ronald'],
      goalkeppers: ['rico', 'hart'],
    },
    encourageTeam() { console.log('We got this!') }
  },
}
```

we can chain operators to access nested properties. We'll have to pay attention to which operator makes sense to use in each layer.

```js
soccerClub.team["youth-team"].forwards; // Returns ['Pedri', 'Konrad']
```

### For Additional Reading

- [Object Basics MDN](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Basics)
- [Working with Objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects)
- [w3Schools](https://www.w3schools.com/js/js_object_definition.asp)
