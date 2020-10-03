# SCOPE

Scope defines where variables can be accessed or referenced in a program. Some variables can be accessed from anywhere within a program, while other variables may only be available in a specific context.

## Block

A block is the code enclosed inside a set of curly braces `{}`. Blocks help in grouping one or more statements together and serve as an important structural marker for our code.

A block of code could be a function, like below:

```js
const tellThePeriod = () => {
  let period = 'morning';
  console.log(period); // morning
};
```

We can Notice that the function body is actually a block of code.

When we also observe the block in an `if` statement:

```js
if (dusk) {
  let period = 'evening';
  console.log(period); // evening
};
```

## Global Scope

variables can exist either outside of or within blocks.

When a variable is declared outside of blocks, the variable is said to be globally scoped. These variables are referred to as global variables. As global variables are not bound inside a block, they can be accessed by any code in the program, including code in blocks.

Taking a look at an example of global scope:

```js
const period = 'morning'

const returnPeriod = () => {
  return period; // morning
};

console.log(returnPeriod()); // morning
```

We can see that even though the `period` variable is defined outside of the block, it can be accessed in the function block, making it a globally scoped variable.
Therefore, `color` can be accessed within the `returnPeriod` function block.


## Block Scope

A variable defined inside a block is said to be block scoped as it is only accessible to the code within the curly braces `{}`. 
Variables that are declared with block scope are known as **"local variables"** because they are only available to the code that is part of the same block.

Taking a example below:

```js
const tellThePeriod = () => {
  let period = 'afternoon';
  console.log(period); // afternoon
};

tellThePeriod(); // afternoon
console.log(period); // ReferenceError
```

We’ll notice that within the function `tellThePeriod`, the `period` variable is only available within the curly braces of the function. When we tried to log the same variable outside the function, we get a `ReferenceError`


## Scope Pollution

Having too many global variables can cause problems in a program.

Global variables when declared, go to the global namespace. This global namespace allows the accessibility of these variables from anywhere in the program. Global namespace can fill up really quickly as these variables remain there until the program finishes

Scope pollution having too many global variables existing in the global namespace, or reusing variables across different scopes. This can make it difficult to keep track of our variables as globally scoped variables can collide with other variables that are more locally scoped, causing unexpected behavior in our code.

Taking a look at an example of scope pollution:

```js
let number = 77;

const logNumber = () => {
  number = 157;
  console.log(number);
};

logNumber(); // Prints 157
console.log(number); // Prints 157

```

Notice That:

- We first declared a variable `number` with the `let` keyword which means the variable can be reassigned another value.

- Inside the function `logNumber()`, we mistakenly reassigned the value of `number` to `157` perhaps we intended to name the variable as something else.

- When `logNumber()` was called, `number` gets reassigned to `157`, which affected the global variable `num`

- We won’t get an error as reassignment is allowed here, so if we decided to use `number` later on, we’ll be using the new value of `number`.

With this it is better not to always make every variable to be globally scoped.

Block scoped variables allows defining variables with precision, and not pollute the global namespace hence If a variable does not need to exist outside a block— it shouldn’t!.
