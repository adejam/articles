# FUNCTIONS

A function is a reusable block of code that groups together a sequence of statements to perform a specific task.

The article does the following:

- Function Declarations.
- How to call a function.
- Function parameters and arguments.
- Default parameters.
- `return` keyword.
- Helper functions.
- Functions expressions.
- Arrow functions.
- Concise body arrow function
- Using functions to solve coding challenges

## Function Declarations

There is more than one way to create a function in Javascript, One way is to use a function declaration. A function declaration binds a function to a name or an identifier.

```js
function greetJamiu() {
  console.log('Hello, Jamiu!');
}
```

A function declaration consists of:

- The `function` keyword.

- The name of the function, or its identifier, is followed by parentheses.

- A function body, or the block of statements required to perform a specific task, enclosed in the function’s curly brackets, `{ }`.

A function declaration is a function that is bound to an identifier, or name.

When using a function, we should always be aware of the [Javascript hoisting](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting) feature which allows access to function declarations before they’re defined.

Taking a look at the example of hoisting below:

```js
console.log(greetJamiu()); // Output: Hello, Jamiu!

function greetJamiu() {
  console.log('Hello, Jamiu!');
}
```

Hoisting allowed `greetJamiu()` to be called before the `greetJamiu()` function was defined! Since hoisting isn’t considered good practice, it is good to be aware of this feature.

We can also determine if a variable is a function by using the `typeof` keyword like below:

```js
function greetJamiu() {
  console.log('Hello, Jamiu!');
}

console.log(typeof greetJamiu); // Output: function
```

## Calling a Function

A function declaration binds a function to an identifier. However, a function declaration does not ask the code inside the function body to run, it just declares the existence of the function. The code inside a function body runs, or executes, only when the function is called.

To call a function in a code, the function name followed by parentheses is to be called.

The same function can be called as many times as needed.

```js
function introduceYourself() {
  console.log('I am adeleye jamiu.');
}

introduceYourself();
introduceYourself();
introduceYourself();
//logs 'Thank you for your purchase! We appreciate your business.' three(3) times.
```

## Parameters and Arguments

Functions can take inputs and use the inputs to perform a task. When declaring a function, I can specify its parameters.

Parameters allow functions to accept input(s) and perform a task using the input(s) in the function body. We use parameters as placeholders for information that will be passed to the function when it is called.

```js
const a = 10;
const b = 15;
function addTwoNumbers(a, b) {
  console.log(a + b);
}
addTwoNumbers(a, b); // outputs: 25
```

In the code above, `addTwoNumbers()`, adds two numbers. The parameters specified between the parenthesis are `a` and `b`, and inside the function body, they act just like regular variables. `a` and `b` act as placeholders for the numbers that will be added.

When calling a function that has parameters, When we called the `addTwoNumbers()` function, we specify the value in the parentheses that follow the function name. The values that are passed to the function when it is called are called arguments. Arguments can be passed to the function as values or variables.

By using parameters, `addTwoNumbers()` can be reused to add any two numbers.

## Default Parameters

When using a function, we can specify a default value. Default parameters allow parameters to have a predetermined value in case there is no argument passed into the function or if the argument is `undefined` when called.

Take a look at the code snippet below that uses a default parameter:

```js
function greeting(name = 'stranger') {
  console.log(`Hello, ${name}!`);
}

greeting('Jamiu'); // Output: Hello, Jamiu!
greeting(); // Output: Hello, stranger!
```

- In the example above, we used the `=` operator to assign the parameter `name` a default value of `'stranger'`. This is useful to have in case we ever want to include a non-personalized default greeting!

- When the code calls `greeting('Jamiu')` the value of the argument is passed in and, `'Jamiu'`, will override the default parameter of `'stranger'` to log `'Hello, Jamiu!'` to the console.

When there isn’t an argument passed into `greeting()`, the default value of `'stranger'` is used, and `'Hello, stranger!'` is logged to the console.

By using a default parameter, we account for situations when an argument isn’t passed into a function that is expecting an argument.

## Return

When a function is called, the computer will run through the function’s code and evaluate the result of calling the function. By default, that resulting value is `undefined`.

```js
function addTwoNumbers(a, b) {
  let result = a + b;
}
console.log(addTwoNumbers(5, 7)); // Prints undefined
```

In the code example, we defined our function `addTwoNumbers` to add two numbers with `a` and `b` as parameters. Then `addTwoNumbers()` is invoked with the arguments `5` and `7`. But when printed the results we got `undefined`. This is like that because we didn't return the value of `result`. In other words, we use the `return` keyword to pass back information from the function call.

To create a return statement, we use the return keyword followed by the value that we wish to return. Like we saw above, if the value is omitted, `undefined` is returned instead.

When a `return` statement is used in a function body, the execution of the function is stopped and the code that follows it will not be executed.

A Look at the example below:

```js
function addTwoNumbers(a, b) {
  if (a < 0 || b < 0) {
    return 'You can only add positive integers!';
  }
  return a + b;
}
```

If an argument for `a` or `b` is less than `0`, then `addTwoNumbers()` will return `'You can only add positive integers!!'`. The second return statement `a + b` will not run.

The `return` keyword is powerful because it allows functions to produce an output. We can then save the output to a variable for later use.

## Helper Functions

The return value of a function can also be used inside another function. These functions being called within another function are often referred to as **helper functions**. Since each function is carrying out a specific task, it makes our code easier to read and debug if necessary.

If we wanted to define a function that converts the temperature from Celsius to Fahrenheit, we could write two functions like:

```js
function multiplyByNineFifths(number) {
  return number * (9 / 5);
}

function getFahrenheit(celsius) {
  return multiplyByNineFifths(celsius) + 32;
}

getFahrenheit(15); // Returns 59
```

In the example above:

- `getFahrenheit()` is called and `15` is passed as an argument.

- The code block inside of `getFahrenheit()` calls `multiplyByNineFifths()` and passes `15` as an argument.

- `multiplyByNineFifths()` takes the argument of `15` for the `number` parameter.

- The code block inside of `multiplyByNineFifths()` function multiplies `15` by `(9/5)`, which evaluates to `27`.

- `27` is returned back to the function call in `getFahrenheit()`.

- `getFahrenheit()` continues to execute. It adds `32` to `27`, which evaluates to `59`.

- Finally, `59` is returned to the function call `getFahrenheit(15)`.

We can use functions to section off small bits of logic or tasks, then use them when we need to. Writing helper functions can help take large and difficult tasks and break them into smaller and more manageable tasks.

## Function Expressions

Another way to define a function is to use a function expression. To define a function inside an expression, we can use the `function` keyword. In a function expression, the function name is usually omitted. A function with no name is called an anonymous function. A function expression is often stored in a variable in order to refer to it.

```js
const addTwoNumbers = function(a, b) {
  let result = a + b;
  return result;
};
```

To declare a function expression:

1. Declare a variable to make the variable’s name i.e `addTwoNumbers` be the name, or identifier, of the function.

2. Then we can assign as that variable’s value an anonymous function created by using the `function` keyword followed by a set of parentheses with possible parameters. Then a set of curly braces that contain the function body.

To invoke a function expression, write the name of the variable in which the function is stored followed by parentheses enclosing any arguments being passed into the function.

```js
addTwoNumbers(a, b);
```

Unlike function declarations, function expressions are not hoisted so they cannot be called before they are defined.

## Arrow Functions

An arrow function is a shorter way to write functions by using the special “fat arrow” `() =>` notation.

Arrow functions remove the need to type out the keyword `function` every time we need to create a function. Instead, we first include the parameters inside the `( )` and then add an arrow `=>` that points to the function body surrounded in `{ }` like below:

```js
const addTwoNumbers = (a, b) => {
  const result = a + b;
  return result;
};
```

## Concise Body Arrow Functions

We can also refactor the arrow function syntax. The most condensed form of the function is known as the concise body.

- Zero Parameters

```js
const functionName = () => {};
```

- One Parameter

```js
const functionName = paramOne => {};
```

- Two Parameters

```js
const functionName = (paramOne, paramTwo) => {};
```

1. Functions that take only a single parameter do not need that parameter to be enclosed in parentheses. However, if a function takes zero or multiple parameters, parentheses are required.

2. A function body composed of a single-line block does not need curly braces. Without the curly braces, whatever that line evaluates will be automatically returned. The contents of the block should immediately follow the arrow `=>` and the `return` keyword can be removed. This is referred to as _implicit return_.

- Single-line block

```js
const addTwoNumbers = a => a + a;
```

- Multi-line block

```js
const addTwoNumbers = (a, b) => {
  const result = a + b;
  return result;
};
```

So if we have a function:

```js
const sayHello = name => {
  return `Hello ${name}`;
};
```

We can refactor the function to:

```js
const sayHello = name => `Hello ${name}`;
```

## Using functions to solve coding challenges

Functions with all its rich features can be used to solve coding challenges which will make code reuseable in other instances.

Considering the [simple array sum](https://www.hackerrank.com/challenges/simple-array-sum/problem) coding challenge from [hackerrank.com](https://www.hackerrank.com/) where we have to write a code which will return the sum of all elements in an [array]().

```js
function simpleArraySum(ar) {
  let sum = 0;
  for (let i = 0; i < ar.length; i++) {
    sum += ar[i];
  }
  return sum;
}
const firstArrayToSum = [1, 2, 3, 4, 5];
const secondArrayToSum = [10, 27, 31, 40, 9];
const thirdArrayToSum = [111, 206, 745, 321, 587];

console.log(simpleArraySum(firstArrayToSum)); // Output: 15
console.log(simpleArraySum(secondArrayToSum)); // Output: 117
console.log(simpleArraySum(thirdArrayToSum)); // Output: 1970
```

From the code above:

- We created a function `simpleArraySum` and in it we initialized a [variable]() `sum` with the `let` keyword to be `0`.

- Then we used a `for` loop to [loop]() through whatever array that is being passed into the function

- In the loop, we add each element of the array to the current value `sum`.

- The we `return` the final value of `sum` which is the summation of all the elements in the array.

It can be noticed that we can reuse this code with whatever array is being passed to the function

## For Further Reading

- [W3schools JavaScript Functions](https://www.w3schools.com/js/js_functions.asp)
- [MDN Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)
- [MDN documentation on hoisting](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting).
