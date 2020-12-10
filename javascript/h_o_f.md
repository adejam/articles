# HIGHER-ORDER-FUNCTIONS

Higher-order functions are functions that accept other functions as arguments and/or return functions as output.

The article does the following:

- Explain Abstraction in programming
- Explain functions as data
- Explain functions as parameters

## Abstraction in Programming

In software engineering and programming language theory, the abstraction principle (or the principle of abstraction) is a basic dictum that aims to reduce duplication of information in a program (usually with an emphasis on code duplication) whenever practical by making use of abstractions provided by the programming language or software libraries.
Retrived from [wikipedia](<https://en.wikipedia.org/wiki/Abstraction_principle_(computer_programming)>).

In addition to allowing reuse of code, [functions]() help to make clear, readable programs.
A level of abstraction can be added to programming through "higher-order functions". This enables building abstractions on other abstractions, just like “We are a programmer” is an abstraction that may build on the abstraction “We have learned at least one programming language.”

In summary, using more abstraction in code allows writing more modular code that is easier to read and debug.

## Functions as Data

Functions like any other data type can be assigned to variables, and can then be reassigned to new variables.

Say we have a function with a long name that repeatedly does some important work in our program like below

```js
const iAmAFunctionWithAnImportantTask = () => {
  console.log('I have an important task to execute!');
};
```

Having to repeat a function name as long as `iAmAFunctionWithAnImportantTask` many times can affect the readability of any code hence we can re-assign the function to another variable. This way we won't be sacrificing the source code.

```js
const important = iAmAFunctionWithAnImportantTask;

important(); //Outputs: I have an important task to execute!
// The above function call barely takes any space!
```

`important` variable holds a reference to the original function. The address in memory of `important` and the address in memory of `iAmAFunctionWithAnImportantTask` would point to the same place. The new `important()` function can be invoked with parentheses as if that was the name originally given to the function.

`iAmAFunctionWithAnImportantTask` Was assigned without parentheses as the value to the `important` variable. The value of the function itself is to be assigned, not the value it returns when invoked.

Functions are first-class objects in JavaScript. This means that, as other objects encountered, JavaScript functions can have properties and methods.

Since functions are a type of object, they have properties such as `.length` and `.name` and methods such as `.toString()`.

Functions can be invoked, but they can still be treated like any other type of data.

```js
const iAmAFunctionWithAnImportantTask = () => {
  console.log('I have an important task to execute!');
};

const important = iAmAFunctionWithAnImportantTask;

important(); // Outputs: I have an important task to execute!

console.log(important.name);
// Output: iAmAFunctionWithAnImportantTask
```

logging `important` with the `.name` property checks the real name of the function.

## Functions as Parameters

Since functions can behave like any other type of data in JavaScript, it can also pass (into other functions) as parameters.
A higher-order function is a function that either accepts functions as parameters, returns a function, or both. We call the functions that get passed in as parameters and invoked callback functions because they get called during the execution of the higher-order function.
Retrived from [codecademy](https://codecademy.com)).

A function when passed in as an argument to another function should not be invoked as invoking the function would evaluate the return value of that function call. With callbacks, the function itself is passed by typing the function name without the parentheses (that would evaluate the result of calling the function):

Say we are to solve two different problems in which we would have to multiply the result of the addition of two numbers and subtraction of the two numbers and divide the result of the addition of the two numbers and subtraction of the two numbers

```js
function solveMultiplication() {
  const additionOfTwoNumbers = 15 + 5;
  const subtractionOfTwoNumbers = 15 - 5;
  return additionOfTwoNumbers * subtractionOfTwoNumbers;
}

function solveDivision() {
  const additionOfTwoNumbers = 15 + 5;
  const subtractionOfTwoNumbers = 15 - 5;
  return additionOfTwoNumbers / subtractionOfTwoNumbers;
}

console.log(solveMultiplication()); //Outputs: 200
console.log(solveDivision()); // Outputs: 2
```

We can notice we had to repeat some `additionOfTwoNumbers` and `subtractionOfTwoNumbers`. Say we want to use these variables in other places in our code we would have to be repeating them in every case.

The code above can then be refactored like below:

```js
function addTwoNumbers() {
  const result = 15 + 5;
  return result;
}

function subtractTwoNumbers() {
  const result = 15 - 5; // assuming the value of a is always greater than the value of b
  return result;
}

function solveMultiplication(addTwoNumbers, subtractTwoNumbers) {
  return addTwoNumbers() * subtractTwoNumbers();
}

function solveDivision(addTwoNumbers, subtractTwoNumbers) {
  return addTwoNumbers() / subtractTwoNumbers();
}

console.log(solveMultiplication(addTwoNumbers, subtractTwoNumbers)); //Outputs: 99
console.log(solveDivision(addTwoNumbers, subtractTwoNumbers));
```

The refactored code seems longer but this way we avoid repeating our codes and we can reuse `addTwoNumbers` and `subtractTwoNumbers` anywhere else in our code.

`solveMultiplication` and `solveDivision` are higher-order function which takes other functions as arguments.

## Below are some resources you can look up for further read

- [Methods and properties of functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function).

- [First-class-Function](https://developer.mozilla.org/en-US/docs/Glossary/First-class_Function)

- [Function-parameters](https://www.w3schools.com/js/js_function_parameters.asp)
