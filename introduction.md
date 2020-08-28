# INTRODUCTION TO JAVASCRIPT

The objective of this article is to present an introduction to the Javascript programming language.

This Article does the following:

- Explain Console in Javascript
- Explain Comments in javascript
- Explain Data Types in Javascript
- Explain Arithmetic Operators in Javascript
- Explain String concatenation in Javascript
- Explain Properties in Javascript
- Explain Methods in Javascript
- Explain Built-In-Objects in Javascript.

JavaScript is a powerful, flexible, and fast programming language being used for web development and beyond!

## console

The console is a panel that displays important messages to the debugging console of our browsers.

In JavaScript, the `console` keyword is an object, a collection of data and actions, that we can use in our code. Keywords are words that are built into the JavaScript language, that the computer will recognize and treat specially.

One action, or method, that is built into the `console` object is the `.log()` method. When we write `console.log()` the parameter passed inside the parentheses will get printed, or logged, to the console.

```javascript
console.log('Jamiu');
```

This example logs `Jamiu` to the console. The semicolon denotes the end of the line or statement. Although in JavaScript our code will usually run as intended without a semicolon, it is recommended to end each statement with a semicolon so we never leave one out in the few instances when they are required. `console.log()` can be used to print different types of data.

## Comments

Comments can explain what the code is doing, leave instructions for developers using the code, or add any other useful annotations.

There are two types of code comments in JavaScript:

- A single line comment will comment out a single line and is denoted with two forward slashes `//` at the beginning or after a line of code.

```javascript
// Prints Jamiu to the console
console.log(Jamiu);
console.log(Jamiu);  // Prints Jamiu
```

- A multi-line comment will comment out multiple lines and is denoted with `/*` to begin the comment, and `*/` to end the comment.

```javascript
/*
This is all commented
console.log(Jamiu);
None of this is going to run!
console.log(Adeleye);
*/
```

This syntax can also be used to comment something out in the middle of a line of code:

```javascript
console.log(/*IGNORED!*/ Jamiu);  // Still just prints Jamiu
```

## Data Types

Data types are the classifications of the different kinds of data that are used in programming. In JavaScript, there are seven fundamental data types:

- Number: Any number, including numbers with decimals: `4`, `8`, `1516`, `23.42`.

- String: Any grouping of characters on our keyboard (letters, numbers, spaces, symbols, etc.) surrounded by single quotes: `' ... '` or double quotes `" ... "`.

- Boolean: This data type only has two possible values— either `true` or `false` (without quotes). It’s helpful to think of booleans as on and off switches or as the answers to a “yes” or “no” question.

- Null: This data type represents the intentional absence of a value, and is represented by the keyword `null` (without quotes).

- Undefined: This data type is denoted by the keyword `undefined` (without quotes). It also represents the absence of a Value though it has a different use than `null`.

- Symbol: A newer feature to the language, symbols are unique identifiers, useful in more complex coding.

- Object: Collections of related data.


The first 6 of those types are considered primitive data types. They are the most basic data types in the language. Objects are more complex.


## Arithmetic Operators

An operator is a character that performs a mathematical operational task in our code. JavaScript has several built-in arithmetic operators, that allow us to perform mathematical calculations on numbers. These include the following operators and their corresponding symbols:

- Add: `+`

- Subtract: `-`

- Multiply: `*`

- Divide: `/`

- Reminder: `%`


```javascript
console.log(3 + 4); // Prints 7
console.log(5 - 1); // Prints 4
console.log(4 * 2); // Prints 8
console.log(9 / 3); // Prints 3
console.log(11 % 3); // Prints 2
```

The remainder operator, sometimes called modulo, returns the number that remains after the right-hand number divides into the left-hand number as many times as it evenly can: `11 % 3` equals `2` because `3` fits into `11` three times, leaving `2` as the remainder.


## String Concatenation

The process of appending one string to another is called concatenation.

```javascript
console.log('hi' + 'ya'); // Prints 'hiya'
console.log('wo' + 'ah'); // Prints 'woah'
console.log('I love to ' + 'code.') // Prints 'I love to code.'
```

Just like with regular math, we can combine, or chain, our operations to get a final result:

```javascript
console.log('One' + ', ' + 'two' + ', ' + 'three!'); // Prints 'One, two, three!'
```

## Properties

Properties are used to check pieces of information on a data type.

Every string instance has a property called `length` that stores the number of characters in that string. we can retrieve property information by appending the string with a period and the property name:

```javascript
console.log('Teaching the world how to code'.length); // prints 30
```

The `.` is another operator! We call it the dot operator.

In the example above, the value saved to the `length` property is retrieved from the instance of the string, `'Teaching the world how to code'`. The program prints 30 to the console because `'Teaching the world how to code'` has thirty characters in it.

## Methods

Methods are actions we can perform. JavaScript provides several string methods.

these methods are called, or used by appending an instance with a period (the dot operator), the name of the method, and opening and closing parentheses: e.g. `'example string'.methodName()`.

When we use `console.log()` we’re calling the `.log()` method on the `console` object.

Some methods are explained below:

- `.toUpperCase()` method: This method returns a string in all capital letters.

```javascript
console.log('hello'.toUpperCase()); // Prints 'HELLO'
```
 `.toUpperCase()` method is called on the string instance `'hello'`. The result is logged to the console. This method returns a string in all capital letters: `'HELLO'`.

- `.startsWith()` method:

  This method takes in an argument as checks if the string to which it is appended starts with that argument. If it starts with the argument then it prints `true` and if it does not start with the argument it prints `false`.

```javascript
console.log('Hey'.startsWith('H')); // Prints true
```

the `.startsWith()` method is called on the string instance `'Hey`'. This method also accepts the character `'H'` as an input, or argument, between the parentheses. Since the string `'Hey'` does start with the letter `'H'`, the method returns the boolean `true`.


- `.trim()` method
 The `.trim()` method is used to remove white spaces at the beginning and end of a string.

 ```js
console.log('    Remove whitespace   '.trim());
 ```

## Built-in Objects

In addition to console, there are other [objects built into JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects). These objects have methods.
For example, the built-in `Math` object in javascript is used to perform more complex mathematical operations than arithmetic. An example is calling the `.random()` method from the built-in Math object:

```js
console.log(Math.random()); // Prints a random number between 0 and 1
```

In the example above, we called the `.random()` method by appending the object name with the dot operator, the name of the method, and opening and closing parentheses. This method returns a random number between 0 and 1.

To generate a random number between 0 and 50, we could multiply this result by 50, like below:

```js
Math.random() * 50;
```
The example above will likely evaluate to a decimal. To ensure an answer is a whole number, we can take advantage of another useful Math method called ```Math.floor()```.

`Math.floor()` takes a decimal number, and rounds down to the nearest whole number. we can use `Math.floor()` to round down a random number like below:

```js
Math.floor(Math.random() * 50);
```

`Math.ceil()` takes a decimal number, and rounds up to the nearest whole number. we can use `Math.ceil()` to round up a random number like this:

```js
Math.ceil(Math.random() * 50);
```

- To see all of the properties and methods on the Math object, take a look at [the documentation here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math).

- check the list of built-in string methods in the [JavaScript documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String).