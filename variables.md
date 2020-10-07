# VARIABLES

A variable is a container for storing data. It is used to label data with a descriptive name. Variables are not values instead they contain values and represent them with a name.

The article does the following:

- Explain how to create Variables in Javascript using "var" and "let" keywords
- Explain the similarities between "var" and "let" keywords.
- Explain dissimilarities between "var" and "let" keywords
- Explain how to create Variables in Javascript using "const" keywords.
- Explain the general rules for naming variables.
- Explain the mathematical assignment operators.
- Explain the increment and decrement operator.
- Explain String Concatenation with Variables in Javascript.
- Explain String Interpolation(Template Literals) in Javascript.
- Explain Thereof operator in Javascript.

## Creating a Variable

### `var`

The `var` keyword to create a variable before the introduction of `const` and `let` in ES6.

```js
var myName = "Jamiu";
console.log(myName); // Output: Jamiu
```

### `let`

The `let` keyword was introduced in ES6. The `let` keyword is used to declare a variable that can later be reassigned to a different value.

```js
let sport = "Soccer";
console.log(sport); // Output: Soccer
sport = "Basketballl";
console.log(sport); // Output: Basketball
```

#### Similarities of `var` and `let` keywords

- Both the `var` and `let` can be used to declare a variable without assigning a value to it. In this case, the variable will automatically be initialized with a value of `undefined`:

```js
let field;
console.log(field); // Output: undefined
field = "javascript";
console.log(field); // Output: javascript
```

```js
var field;
console.log(field); // Output: undefined
field = "javascript";
console.log(field); // Output: javascript
```

From the examples above, it can be established that the value of both variables can be reassigned.

#### Disimilarities between `var` and `let` keywords

the difference between them is that `var` is function scoped and `let` is block scoped. example:

```js
console.log(num);
var num = 6;
console.log(num); //Output: undefined, 6
```

if an undeclared variable is logged to the console and later declared with `var` and assigned a value, it will return undefine and the value assigned to it, an error will be returned if `let` is used in declaring such variable. example:

```js
console.log(num); // output: ReferenceError: x is not defined
let num = 6;
console.log(num); //Output: 6
```

### `const`

Just like with `var` and `let` we can store any value in a `const` variable. The way we declare a const variable and assign a value to it follows the same pattern as `let` and `var`.

```js
const myName = "Jamiu";
console.log(myName); // Output: Jamiu
```

However, the difference here is that a `const` variable cannot be reassigned because it is _constant_. If we try to reassign a `const` variable, we’ll get a TypeError.

Constant variables must be assigned a value when declared. If we try to declare a `const` variable without a value, we’ll get a SyntaxError.

- **NOTE**: `let` is the preferred way to declare a variable when we expect the variable to be reassigned, and `const` is the preferred way to declare a variable with a constant value.

### General Rules for Naming Variables:

There are rules to keep in mind when naming variables,

- Variable names cannot start with numbers.

- Variable names are case sensitive, so `myName` and `myname` would be different variables. It is bad practice to create two variables that have the same name using different cases.

- Variable names cannot be the same as keywords. For a comprehensive list of keywords check out [MDN’s keyword documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Keywords).
  By [codecademy.com](https://codecademy.com)

## Mathematical Assignment Operators

Variables and math operators can be used to calculate new values and assign them to a variable.

```js
let num = 7;
num = num + 2;

console.log(w); // Output: 9
```

from the example above the variable, `num` was assigned the value of `7`. Then the `num` variable was reassigned the addition of itself and `1`.

Use built-in mathematical assignment operators is another way that the `num` variable can be reassigned. We could re-write the code above to be:

```js
let num = 7;
num += 2;

console.log(num); // Output: 9
```

In the second example, the `+=` assignment operator is used to reassign `num`. We’re performing the mathematical operation of the first operator `+` using the number to the right, then reassigning `num` to the computed value.

Other mathematical assignment operators we also have access to are: `-=`, `*=`, and `/=` which work similarly.

```js
let num = 25;
num -= 5; // Can be written as num = num - 5
console.log(num); // Output: 20

let numTwo = 50;
numTwo *= 3; // Can be written as numTwo = numTwo * 3
console.log(numTwo); // Output: 150

let numThree = 8;
numThree /= 2; // Can be written as numThree = numThree / 2
console.log(numThree); // Output: 4
```

## The Increment and Decrement Operator

The increment operator will increase the value of the variable by 1. The decrement operator will decrease the value of the variable by 1. For example:

The increment operator is used to increase the value of a variable by 1 while the decrement operator is used to decrease the value of a variable by 1.

```js
let num = 17;
num++;
console.log(num); // Output: 18
```

```js
let numTwo = 20;
numTwo--;
console.log(numTwo); // Output: 19
```

Like the previous mathematical assignment operators (`+=`, `-=`, `*=`, `/=`), the variable’s value is updated and assigned as the new value of that variable.

## String Concatenation with Variables

The String Concatenation operator (`+`) can be used to combine two string values even if those values are being stored in variables:

```js
let myLanguage = "javascript";
console.log("I code in " + myLanguage + "."); // Output: 'I code in javascript.'
```

In the example above, we assigned the value `javascript` to the `myLanguage` variable. On the second line, the `+` operator is used to combine three strings: `I code in `, then the value saved to `myLanguage`, and `.`.

## String Interpolation(Template Literals)

Variables can be inserted or interpolated into strings using template literals. example:

```js
let myLanguage = "javascript";
console.log(`I code in ${myLanguage}.`); // Output: 'I code in javascript.'
```

Notice that:

- in using a template literal we wrapped the whole string by backticks **`**.
- Inside the template literal, we use a placeholder, `${myLanguage}` making The value of `myLanguage` to be inserted into the template literal.
- When we interpolate `I code in ${myLanguage}.`, the output printed is the string: `I code in javascript.`

One of the biggest benefits of using template literals is the readability of the code. Using template literals, one more easily tells what the new string will be. Also, there won't be a need to worry about escaping double quotes or single quotes.

## Typeof Operator

The `typeof` operator is used to check the data type of a variable’s value. It returns a string of the data type of the variable

```js
const tellMeTheType1 = 109;
console.log(typeof tellMeTheType1); // Output: number

const tellMeTheType2 = "Jamiu";
console.log(typeof tellMeTheType2); // Output: string

const tellMeTheType3 = true;
console.log(typeof tellMeTheType3); // Output: boolean
```

## For extra reading:
- [w3schools](https://www.w3schools.com/js/js_variables.asp)
- [mdn](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Variables)
