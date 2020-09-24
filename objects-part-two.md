# LEARNING JAVASCRIPT SERIES: JAVASCRIPT OBJECTS Part 2

This objective of this article is to  explain:

- Pass by reference.
- Looping through objects.
- The `this` keyword.
- The arrow function and `this`.
- Privacy in Objects.


## Pass By Reference

Objects are _passed by reference_. This means when a variable assigned to an object is passed into a function as an argument, the computer interprets the parameter name as pointing to the space in memory holding that object. As a result, functions that change object properties actually mutate the object permanently (even when the object is assigned to a `const` variable).

```js
const name = {
  firstname: "Adeleye",
  course: "javascript",
};

let changeCourse = (obj) => {
  obj.course = "php";
};

changeCourse(name);

name.course; // Returns 'php'
```

Our function `changeCourse()` permanently changed the `course` of our `name` object. However, reassignment of the `name` variable wouldn’t work in the same way:

```js
let name = {
  firstname: "Adeleye",
  course: "javascript",
};
let tryToReassign = (obj) => {
  obj = {
    identified: false,
    "transport type": "car",
  };
  console.log(obj); // Prints {'identified': false, 'transport type': 'car'}
};
tryToReassign(name); // The attempt at reassignment does not work.
name; // Still returns {firstname : 'Adeleye',course : 'javascript'};

name = {
  identified: false,
  "transport type": "car",
}; // Regular reassignment still works.
```

From the code example above:

- Using `let` to declare the `name` object allowed us to reassign it to a new object `identified` and `transport type` properties.

- When we tried the same thing using a function designed to reassign the object passed in to it, the reassignment didn’t stick (even though calling `console.log()` on the object produced the expected result).

- When `name` is passed into that function, `obj` became a reference to the memory location of the `name` object, but not to the `name` variable. This is because the `obj` parameter of the `tryToReassign()` function is a variable in its own right. The body of `tryToReassign()` has no knowledge of the `name` variable at all!

- When we did the reassignment in the body of `tryToReassign()`, the `obj` variable came to refer to the memory location of the object `{'identified' : false, 'transport type' : 'flying'}`, while the `name` variable was completely unchanged from its earlier value.

## Looping Through Objects

We can loop through objects using the [`for...in`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...in) loop.

`for...in` will execute a given block of code for each property in an object.

```js
let soccerClub = {
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
// for...in
for (let teamMembers in soccerClub.team) {
  console.log(`${teamMembers}: ${soccerClub.team[teamMembers].forwards}`)
};

/*Outputs:
mainTeam: ['Messi', 'Dembele', 'Ansu Fati', 'Trincao', 'Griezmann']
'youth-team': ['Pedri', 'Konrad']
*/
```

The `for...in` will iterate through each element of the `soccerClub.team` object. In each iteration, the variable `teamMembers` is set to one of `soccerClub.team`‘s keys, enabling logging a list of team members’ `forwards`.

## The `this` Keyword

The `this` keyword is used in an object's `method` to reference the `value` of a property in that object which is then used in the method.

```js
const ferrari = {
  fuelType: "petrol",
  makeSound() {
    console.log("zooooom");
  },
};
```

In the ferrari object, we have a `.makeSound()` method. The `.makeSound()` method can be invoked on `ferrari`.

```js
ferrari.makeSound(); // Prints zooooom
```

We have a `ferrari` object that can print `zoooom` to the console. If we wanted to add a new method to the `ferrari` object called `.fuel()` that prints the `ferrari`‘s `fuelType`?

```js
const ferrari = {
  fuelType: "petrol",
  makeSound() {
    console.log("zooooom");
  },
  fuel() {
    console.log(fuelType);
  },
};
ferrari.fuel();
// Output will be "ReferenceError: fuelType is not defined"
```

`fuelType` is not defined even though it’s a property of `ferrari` because, inside the scope of the `.diet()` method, we don’t automatically have access to other properties of the `ferrari` object.

The `this` keyword comes to the rescue here. If we change the `.fuel()` method to use the `this`, the `.fuel()` works! :

```js
const ferrari = {
  fuelType: "petrol",
  makeSound() {
    console.log("zooooom");
  },
  fuel() {
    console.log(this.fuelType);
  },
};
ferrari.fuel();
// Output: petrol
```

The `this` keyword references the _calling_ object which provides access to the calling object’s properties. In the example above, the calling object is `ferrari`and by using `this` we are accessing the `ferrari` object itself, and then the `fuelType` property of `ferrari` by using property dot notation.

## Arrow Functions and this

The `this` keyword becomes a bit more complicated when using arrow functions for methods. Take a look at the example below:

```js
const ferrari = {
  fuelType: 'petrol',
  makeSound() {
    console.log('zooooom');
  },
  fuel = () => {
    console.log(this.fuelType);
  }
};
ferrari.fuel(); // Prints undefined
```

`ferrari.fuel()` log `undefined` as the `.diet()` is defined using an arrow function.

Arrow functions inherently _bind_, or tie, an already defined `this` value to the function itself that is **NOT** the calling object. In the code snippet above, the value of `this` is the _global object_, or an object that exists in the global scope, which doesn’t have a `fuelType` property and therefore returns `undefined`.

To read more about either arrow functions or the global object check out the MDN documentation of the [
global object](https://developer.mozilla.org/en-US/docs/Glossary/Global_object) and [arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions).

The key takeaway from the example above is to **avoid** using arrow functions when using `this` in a method!

## Privacy

There are cases in which we don’t want other code simply accessing and updating an object’s properties. When discussing privacy in objects, we see it as the idea that only certain properties should be mutable or able to change in value.

JavaScript does not have privacy built-in for objects. Rather, developers follow a naming convention that signals to other developers how to interact with a property. One common convention is to place an underscore `_` before the name of a property to mean that the property should not be altered.below is an example of using `_` to prepend a property.

```js
const savings = {
  _amount: 1000,
};
```

In the example above, the `_amount` is not intended to be directly manipulated.

Even so, it is still possible to reassign `_amount`:

```js
bankAccount._amount = 1000000;
```

The use of methods called _getters_ and _setters_ are used to respect the intention of properties prepended, or began, with `_`. _Getters_ can return the value of internal properties and _setters_ can safely reassign property values.

### Extra Reading

- [Object Basics MDN](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Basics)
- [Working with Objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects)
- [w3Schools](https://www.w3schools.com/js/js_object_definition.asp)