# LEARNING JAVASCRIPT SERIES: JAVASCRIPT OBJECTS part 3

This objective of this article is to:

- Explain Getters in Javascript Objects.
- Explain Setters in Javascript Objects.
- Explain Factory functions.
- Explain Property value shorthand.
- Explain destructured assignments.
- Explain some Built-In Object methods.

## Getters

`Getters` are methods that get and return the internal properties of an object. But they can do more than just retrieve the value of a property! Taking a look at a getter method:

```js
const person = {
  _firstName: "Adeleye",
  _lastName: "Jamiu",
  get fullName() {
    if (this._firstName && this._lastName) {
      return `${this._firstName} ${this._lastName}`;
    } else {
      return "Missing a first name or a last name.";
    }
  },
};

// To call the getter method:
person.fullName; // 'Adeleye Jamiu'
```

It is noticeable that in the getter method above:

- We use the `get` keyword followed by a function.

- We use an `if...else` conditional to check if both `_firstName` and `_lastName` exist (by making sure they both return truthy values) and then `return` a different value depending on the result.

- We can access the calling object’s internal properties using this. In `fullName`, we are accessing both `this._firstName` and `this._lastName`.

- In the last line we called `fullName` on `person`.
  In general, getter methods do not need to be called with a set of parentheses. Syntactically, it looks like a property is being accessed.

Some notable advantages of using getter methods:

- Getters can perform an action on the data when getting a property.

- Getters can return different values using conditionals.

- In a getter, the properties of the calling object can be accessed using `this`.

- The functionality of the code is easier for other developers to understand.

When using getter (and setter) methods, properties cannot share the same name as the getter/setter function as that will result in an infinite call stack error. One way around is to add an underscore before the property name as we did in the example above.

## Setters

`Setter` methods reassign the values of existing properties within an object.

```js
const jamiu = {
  _age: 12,
  set age(newAge) {
    if (typeof newAge === "number") {
      this._age = newAge;
    } else {
      console.log("You must assign a number to age");
    }
  },
};
```

In the example above:

- we can perform a check for what value is being assigned to `this._age`.

- When we use the setter method, only values that are numbers will reassign `this._age`.

- Different outputs are depending on what values are used to reassign `this._age`.

Then to use the setter method:

```js
jamiu.age = 50;
console.log(jamiu._age); // Logs: 50
jamiu.age = "50"; // Logs: You must assign a number to age
```

Setter methods like `age` do not need to be called with a set of parentheses. Syntactically, it looks like we are reassigning the value of a property.

Like getter methods, there are similar advantages to using setter methods that include checking input, performing actions on properties, and displaying a clear intention for how the object is supposed to be used. Nonetheless, even with a setter method, it is still possible to directly reassign properties. For example, in the example above, we can still set `._age` directly:

```js
person._age = "forty-five";
console.log(person._age); // Prints forty-five
```

## Factory Functions

Factory functions are used to create many instances of an object. Factory functions can also have parameters that allow us to customize the object that gets returned.

Let’s say we wanted to create an object to represent footballers in JavaScript. There are many different types of footballers and we could go about making each footballer individually but we can also use a factory function to make it easier. To achieve this we can use a factory function that has parameters:

```js
const footballer = (name, age, club, goalCelebration) => {
  return {
    name: name,
    age: age,
    club: club,
    celebrate() {
      console.log(goalCelebration);
    },
  };
};
```

In the `footballer` function above, it has four parameters and returns an object that has the properties: `name`, `age`, `club`, and `strongFoot()`. To make an object that represents a specific footballer like a _striker_, we can call `footballer` with the necessary arguments and assign the return value to a variable:

```js
const striker = footballer("messi", 33, "Barcelona", "goooooooal!");
striker.celebrate(); // 'goooooooal!'
```

Now we have a striker object as a result of calling `footballer()` with the required arguments. With `footballer` in place, we don’t have to create an object literal every time we need a new footballer. Instead, we can invoke the `footballer` function with the necessary arguments.

## Property Value Shorthand

In the previous exercise, we created a factory function that helped create objects. We had to assign each property a key and value even though the key name was the same as the parameter name we assigned to it.

```js
const footballer = (name, age) => {
  return {
    name: name,
    age: age,
  };
};
```

If we had more properties, it would become more tedious to follow the pattern above But we can use a destructuring technique, called _property value shorthand_, to save ourselves some keystrokes. The example below works exactly like the example above:

```js
const footballer = (name, age) => {
  return {
    name,
    age,
  };
};
```

## Destructured Assignment

I often want to extract key-value pairs from objects and save them as variables. Take for example the following object:

```js
const footballer = {
  name: "Messi",
  residence: "Barcelona",
  preferences: {
    sleeves: "short sleeves",
    strongFoot: "left",
  },
};
```

If we wanted to extract the `residence` property as a variable, we could use the following code:

```js
const residence = footballer.residence;
console.log(residence); // Prints 'Barcelona'
```

However, we can also take advantage of a destructuring technique called `destructured assignment` to save ourselves some keystrokes. In a destructured assignment we create a variable with the name of an object’s key that is wrapped in curly braces `{ }` and assign to it the object. Taking a look at the example below:

```js
const { residence } = footballer;
console.log(residence); // Prints 'Barcelona'
```

Look back at the `footballer` object’s properties in the first code example. Then, in the example above, we declare a new variable `residence` that extracts the value of the `residence` property of `vampire`. When we log the value of residence to the console, `'Barcelona'` is printed.

We can even use destructured assignment to grab nested properties of an object:

```js
const { sleeves } = footballer.preferences;
console.log(sleeves); // Prints 'short sleeves'
```

we can also extract multiple properties at once, this can be useful when we only need some particular properties and not all the properties of an object

```js
const { name, sleeves: { strongFoot } } = footballer;
```

## Built-in Object Methods

In the previous exercises, we've been creating instances of objects that have their methods. But, we can also take advantage of built-in methods for Objects!

For example, we have access to object instance methods like: `.hasOwnProperty()`, `.valueOf()`, and many more at [MDN’s object instance documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object#Methods).

There are also useful Object class methods such as `Object.assign()`, `Object.entries()`, and `Object.keys()` just to name a few. For a comprehensive list, we can browse: [MDN’s object instance documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object#Methods_of_the_Object_constructor).

### Extra Reading

- [Object Basics MDN](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Basics)
- [Working with Objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects)
- [w3Schools](https://www.w3schools.com/js/js_object_definition.asp)
