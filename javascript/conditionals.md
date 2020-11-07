# CONDITIONAL STATEMENTS

Conditional statements are statements that check a specific condition(s) and perform a task based on the condition(s).

The article does the following:

- Explain the `if` statement.
- Explain `if...else` statement.
- Explain comparison operators.
- Explain logical operators.
- Explain truthy and falsy.
- Explain truthy and falsy assignment.
- Explain ternary operators.
- Explain `else...if` statements.
- Explain the `switch` keyword.

## If Statement

Often a task will be performed based on a condition. For example, **If** we’re tired, then we’ll rest. another example is **If** our laptop's battery level is below 10% then we want the laptop to hibernate.

This can also be performed in programming using an `if` statement:

```js
const batteryLevel = 7;
if (batteryLevel <= 10) {
  console.log('I have to hibernate!');
}
// Prints: I have to hibernate!
```

If the condition `(batteryLevel <= 10)` which means `batteryLevel` should be less than or equals to `10` evaluates to `true`, the code inside the curly braces `{}` will be executed and if the condition evaluates to `false`, the block won’t execute. Since our `batteryLevel` is `7` which is less than `10` then the block would run and `I have to hibernate!` will be logged.

## If...Else Statements

Sometimes we would want to add another task in case our `if` statement evaluates to false, this is achieved by using adding the `else` statement to the `if` statement. This is referred to as an `if...else` statement.

```js
const batteryLevel = 11;
if (batteryLevel <= 10) {
  console.log('I have to hibernate!');
} else {
  console.log('I don't have to hibernate at the moment!');
}

// Outputs: I don't have to hibernate at the moment!
```

In the example above, the `batteryLevel` is `11` which is greater than `10` making the statement to be `false` therefore the `else` block will be executed.

## Comparison Operators

Sometimes we would need to use different types of operators to compare values. These operators are referred to as comparison operators.

Below is a list of some handy comparison operators and their syntax:

- Less than: `<`

- Greater than: `>`

- Less than or equal to: `<=`

- Greater than or equal to: `>=`

- Is equal to: `===`

- Is not equal to: `!==`

Comparison operators compare a value on the left with another value on the right. like below:

```js
7 < 10; // Evaluates to true
```

## Logical Operators

There are also operators that work with boolean values(`true` or `false`) which are known as logical operators. These logical operators are used to add more sophisticated logic to our conditionals. There are three logical operators:

- the `and` operator (`&&`)

- the `or` operator (`||`)

- the `not` operator, otherwise known as the bang operator (`!`)

The `&&` operator is used to check that two things are true:

```js
if (firstname === 'Adeleye' && lastname === 'Jamiu') {
  console.log('Adeleye Jamiu');
} else {
  console.log('Unauthorized user!');
}
```

When using the `&&` operator, both conditions must evaluate to `true` for the entire condition to evaluate to `true` and execute. Otherwise, if either condition is `false`, the `&&` condition will evaluate to `false` and the `else` block will execute.

If we need to check for atleast one condition being `true`, we can use the `||` operator:

```js
if (user === 'Adeleye' || user === 'Jamiu') {
  console.log('Authorized user!');
} else {
  console.log('Unauthorized user!');
}
```

When using the `||` operator, only one of the conditions must evaluate to `true` for the overall statement to evaluate to `true`. In the code example above, if either `user === 'Adeleye'` or `user === 'Jamiu'` evaluates to `true` the `if`‘s condition will evaluate to `true` and its code block will execute. If the first condition in an `||` statement evaluates to `true`, the second condition won’t even be checked. Only if `user === 'Adeleye'` evaluates to `false` will `user === 'Jamiu'` be evaluated. The code in the `else` statement above will execute only if both comparisons evaluate to `false`.

The `!` not operator reverses, or negates, the value of a boolean:

```js
let exposed = true;
console.log(!exposed); // Prints false

let covered = false;
console.log(!covered); // Prints true
```

From the above it can be seen that the `!` operator will either take a `true` value and pass back `false`, or it will take a `false` value and pass back `true`.

## Truthy and Falsy

Taking consideration of how non-boolean data-types like strings or numbers are evaluated when checked inside a condition

In cases where we want to check if a variable exists and don't want it to equal a specific value, we can check if the variable has a value like below:

```js
let foodFlask = 'not empty';

if (foodFlask) {
  console.log(foodFlask);
} else {
  console.log('Food flask is empty.');
}

// Prints: not empty
```

The code block in the `if` statement will run because `foodFlask` has a truthy value. Although the value of `foodFlask` is not explicitly the value `true`, it evaluates to `true` because it has been assigned a non-falsy value, when used in a boolean or conditional context,

Below is a list of falsy values:

- `0`

- Empty strings like `""` or `''`

- `null` which represent when there is no value at all

- `undefined` which represent when a declared variable lacks a value

- `NaN`, or Not a Number

Here’s an example with numbers:

```js
let score = 0;

if (score) {
  console.log('you won');
} else {
  console.log('You lose');
}

// Prints 'You lose!'
```

The code block in the `else` statement will run as the condition evaluates to `false` because the value of the `score` is `0` and `0` is a falsy value.

## Truthy and Falsy Assignment

Say I have a website and want to use a user’s username to make a personalized greeting. Sometimes, the user does not have an account, making the `username` variable falsy. The code below checks if `username` is defined and assigns a default string if it is not:

say we want to have a personalized greeting feature on our website, sometime we have a user who is authenticated and sometimes we have a user who is not. We can use the code below to if a user's `username` is defined and assign it his/her name or assign them a default value if `username` is not defined

```js
let assignedName;
if (username) {
  assignedName = username;
} else {
  assignedName = 'Guest';
}
```

Combining the knowledge of logical operators a short-hand can be used for the code above. In a boolean condition, JavaScript assigns the truthy value to a variable if the `||` operator is used in the assignment:

```js
let assignedName = username || 'Guest';
```

Because `||` or statements check the left-hand condition first, the variable `assignedName` will be assigned the actual value of `username` if is truthy, and it will be assigned the value of `'Guest'` if `username` is falsy. This concept is also referred to as **short-circuit evaluation**.

## Ternary Operator

We can also use ternary operators, which is also a short-hand notation

Take a look at the `if...else` statement below:

```js
let isHalfTime = true;

if (isHalfTime) {
  console.log('Take a break!');
} else {
  console.log('Keep Playing!');
}

// Prints: Take a break!
```

We can use a ternary operator to perform the same functionality:

```js
isHalfTime ? console.log('Take a break!') : console.log('Keep Playing!');
```

In the example above:

- The condition, `isHalfTime`, is provided before the `?`.

- Two expressions follow the `?` and are separated by a colon `:`.

- If the condition evaluates to `true`, the first expression executes.

- If the condition evaluates to `false`, the second expression executes.

Like `if...else` statements, ternary operators can be used for conditions that evaluate to `true` or `false`.

## Else If Statements

The `else if` statement can be added to the `if...else` which allows for more than two possible outcomes. We can add as many `else if` statements as we would like, to make more complex conditionals!

The `else if` statement always comes after the `if` statement and before the `else` statement. The `else if` statement also takes a condition.

```js
let grade = 50;

if (grade >= 70) {
  console.log('You passed with a Distinction!');
} else if (grade >= 60 && <= 69) {
  console.log('You passed with an Excellent result!');
} else if (grade >= 50 && <= 59) {
  console.log('You passed with an Average result!');
} else if (grade >= 40 && <= 49) {
  console.log('You passed with a good result!');
} else {
  console.log('You Failed!');
}

// output: You passed with an Average result!
```

`if`/`else if`/`else` statements are read from top to bottom, so the first condition that evaluates to `true` from the top to bottom is the block that gets executed.

## The `switch` keyword

`else if` statements are a great tool if I need to check multiple conditions. In programming, we often find ourselves needing to check multiple values and handling each of them differently. For example:

```js
let shirt = 'Long sleeves';

if (shirt === 'Short sleeves') {
  console.log('Short sleeves are $1.69');
} else if (shirt === 'Long sleeves') {
  console.log('Long sleeves are $3.25');
} else {
  console.log('Invalid shirt');
}

// Prints: Long sleeves are $3.25
```

In the code above, we have a series of conditions checking for a value that matches a `shirt` variable. The code works fine, but imagine if I needed to check 100 different values! Having to write that many `else if` statements sound like a pain!

A switch statement provides an alternative syntax that is easier to read and write. A switch statement looks like below:

```js
let shirt = 'Long sleeves';

switch (shirt) {
  case 'Short sleeves':
    console.log('Short sleeves are $1.69');
    break;
  case 'Long sleeves':
    console.log('Long sleeves are $3.25');
    break;
  case 'Medium sleeves':
    console.log('Medium sleeves are $2.29');
    break;
  default:
    console.log('Invalid shirt');
    break;
}

// Prints 'Long sleeves are $3.25'
```

- The `switch` keyword initiates the statement and is followed by `( ... )`, which contains the value that each `case` will compare. In this case, it is `shirt`.

- Inside the block, `{ ... }`, there are multiple `case`s. The `case` keyword checks if the expression matches the specified value that comes after it. The value following the first `case` is `'Short sleeves'`. If the value of `shirt` equaled `'Short sleeves'`, that `case`‘s `console.log()` would run.

- The value of `shirt` is `'Long sleeves'`, so the second `case` runs— `Long sleeves are $3.25` is logged to the console.

- The `break` keyword tells the computer to exit the block and not execute any more code or check any other cases inside the code block.

  Note: Without the `break` keyword at the end of each case, the program would execute the code for all matching cases and the default code as well. This behavior is different from `if/else` conditional statements that execute only one block of code.

- At the end of each `switch` statement, there is a `default` statement. If none of the `case`s are true, then the code in the `default` statement will run.

## For extra reading

- [mdn](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/conditionals)
- [w3schools if and if/else statements](https://www.w3schools.com/js/js_if_else.asp)
- [w3schools switch statements](https://www.w3schools.com/js/js_switch.asp)
