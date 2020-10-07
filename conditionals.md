# CONDITIONAL STATEMENTS

Conditional statements are statements that checks a specific condition(s) and performs a task based on the condition(s).

## If Statement

Often a task will performed based on a condition. For example, **If** we’re tired, then we’ll rest. another example is **If** our laptop's battery level is below 10% then we want the laptop to hibernate.

This can also be performed in programming using an `if` statement:

```js
const batteryLevel = 7;
if (batteryLevel <= 10) {
  console.log("I have to hibernate!");
}
// Prints: I have to hibernate!
```

If the condition `(batteryLevel <= 10)` which means `batteryLevel` shold be less than or equals to `10` evaluates to `true`, the code inside the curly braces `{}` will be executed and if the condition evaluates to `false`, the block won’t execute. Since our `batteryLevel` is `7` which is less than `10` then the block would run and `I have to hibernate!` will be logged.

## If...Else Statements

Sometimes we would want to add another task incase our `if` statement evaluates to false, this is achieved by using adding `else` statement to the `if` statement. This is referred to as an `if...else` statement.

```js
const batteryLevel = 11;
if (batteryLevel <= 10) {
  console.log("I have to hibernate!");
} else {
  console.log("I dont have to hibernate at the moment!");
}

// Outputs: I dont have to hibernate at the moment!
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
if (firstname === "Adeleye" && lastname === "Jamiu") {
  console.log("Adeleye Jamiu");
} else {
  console.log("Unauthorized user!");
}
```

When using the `&&` operator, both conditions must evaluate to `true` for the entire condition to evaluate to `true` and execute. Otherwise, if either condition is `false`, the `&&` condition will evaluate to `false` and the `else` block will execute.

If we need to check for atleast one condition being `true`, we can use the `||` operator:

```js
if (user === "Adeleye" || user === "Jamiu") {
  console.log("Authorized user!");
} else {
  console.log("Unauthorized user!");
}
```

When using the `||` operator, only one of the conditions must evaluate to `true` for the overall statement to evaluate to `true`. In the code example above, if either `day === 'Saturday'` or `day === 'Sunday'` evaluates to `true` the `if`‘s condition will evaluate to `true` and its code block will execute. If the first condition in an `||` statement evaluates to `true`, the second condition won’t even be checked. Only if `day === 'Saturday'` evaluates to `false` will `day === 'Sunday'` be evaluated. The code in the `else` statement above will execute only if both comparisons evaluate to `false`.

The `!` not operator reverses, or negates, the value of a boolean:

```js
let excited = true;
console.log(!excited); // Prints false

let sleepy = false;
console.log(!sleepy); // Prints true
```

Essentially, the `!` operator will either take a `true` value and pass back `false`, or it will take a `false` value and pass back `true`.

Logical operators are often used in conditional statements to add another layer of logic to our code.

## Truthy and Falsy

Considering how non-boolean data types, like strings or numbers, are evaluated when checked inside a condition.

Sometimes, it is possible to check if a variable exists and won’t necessarily want it to equal a specific value — one will only check to see if the variable has been assigned a value.

Here’s an example:

```
let myVariable = 'I Exist!';

if (myVariable) {
   console.log(myVariable)
} else {
   console.log('The variable does not exist.')
}
```

The code block in the `if` statement will run because `myVariable` has a truthy value; even though the value of `myVariable` is not explicitly the value `true`, when used in a boolean or conditional context, it evaluates to `true` because it has been assigned a non-falsy value.

So which values are falsy— or evaluate to `false` when checked as a condition? The list of falsy values includes:

- `0`

- Empty strings like `""` or `''`

- `null` which represent when there is no value at all

- `undefined` which represent when a declared variable lacks a value

- `NaN`, or Not a Number

Here’s an example with numbers:

```
let numberOfApples = 0;

if (numberOfApples){
   console.log('Let us eat apples!');
} else {
   console.log('No apples left!');
}

// Prints 'No apples left!'
```

The condition evaluates to `false` because the value of the `numberOfApples` is `0`. Since `0` is a falsy value, the code block in the `else` statement will run.

## Truthy and Falsy Assignment

Truthy and falsy evaluations open a world of short-hand possibilities!

Say i have a website and want to take a user’s username to make a personalized greeting. Sometimes, the user does not have an account, making the `username` variable falsy. The code below checks if `username` is defined and assigns a default string if it is not:

```
let defaultName;
if (username) {
  defaultName = username;
} else {
  defaultName = 'Stranger';
}
```

Combining the knowledge of logical operators a short-hand can be used for the code above. In a boolean condition, JavaScript assigns the truthy value to a variable if the `||` operator is used in the assignment:

```
let defaultName = username || 'Stranger';
```

Because `||` or statements check the left-hand condition first, the variable `defaultName` will be assigned the actual value of `username` if is truthy, and it will be assigned the value of `'Stranger'` if `username` is falsy. This concept is also referred to as short-circuit evaluation.

## Ternary Operator

In the spirit of using short-hand syntax, i can use a ternary operator to simplify an `if...else` statement.

Take a look at the `if...else` statement example:

```
let isNightTime = true;

if (isNightTime) {
  console.log('Turn on the lights!');
} else {
  console.log('Turn off the lights!');
}
```

I can use a ternary operator to perform the same functionality:

```
isNightTime ? console.log('Turn on the lights!') : console.log('Turn off the lights!');
```

In the example above:

- The condition, `isNightTime`, is provided before the `?`.

- Two expressions follow the `?` and are separated by a colon `:`.

- If the condition evaluates to `true`, the first expression executes.

- If the condition evaluates to `false`, the second expression executes.

Like `if...else` statements, ternary operators can be used for conditions which evaluate to `true` or `false`.

## Else If Statements

More conditions can be added to the `if...else` with an `else if` statement. The `else if` statement allows for more than two possible outcomes. I can add as many `else if` statements as i would like, to make more complex conditionals!

The `else if` statement always comes after the `if` statement and before the `else` statement. The `else if` statement also takes a condition. Taking a look at the syntax:

```
let stopLight = 'yellow';

if (stopLight === 'red') {
  console.log('Stop!');
} else if (stopLight === 'yellow') {
  console.log('Slow down.');
} else if (stopLight === 'green') {
  console.log('Go!');
} else {
  console.log('Caution, unknown!');
}
```

The `else if` statements allows for multiple possible outcomes. `if`/`else if`/`else` statements are read from top to bottom, so the first condition that evaluates to `true` from the top to bottom is the block that gets executed.

In the example above, since `stopLight === 'red'` evaluates to `false` and `stopLight === 'yellow'` evaluates to `true`, the code inside the first `else if` statement is executed. The rest of the conditions are not evaluated. If none of the conditions evaluated to `true`, then the code in the `else` statement would have executed.

## The `switch` keyword

`else if` statements are a great tool if i need to check multiple conditions. In programming, we often find ourselves needing to check multiple values and handling each of them differently. For example:

```
let groceryItem = 'papaya';

if (groceryItem === 'tomato') {
  console.log('Tomatoes are $0.49');
} else if (groceryItem === 'papaya'){
  console.log('Papayas are $1.29');
} else {
  console.log('Invalid item');
}
```

In the code above, i have a series of conditions checking for a value that matches a `groceryItem` variable. The code works fine, but imagine if i needed to check 100 different values! Having to write that many `else if` statements sounds like a pain!

A switch statement provides an alternative syntax that is easier to read and write. A switch statement looks like this:

```
let groceryItem = 'papaya';

switch (groceryItem) {
  case 'tomato':
    console.log('Tomatoes are $0.49');
    break;
  case 'lime':
    console.log('Limes are $1.49');
    break;
  case 'papaya':
    console.log('Papayas are $1.29');
    break;
  default:
    console.log('Invalid item');
    break;
}

// Prints 'Papayas are $1.29'
```

- The `switch` keyword initiates the statement and is followed by `( ... )`, which contains the value that each `case` will compare. In the example, the value or expression of the `switch` statement is `groceryItem`.

- Inside the block, `{ ... }`, there are multiple `case`s. The `case` keyword checks if the expression matches the specified value that comes after it. The value following the first `case` is `'tomato'`. If the value of `groceryItem` equalled `'tomato'`, that `case`‘s `console.log()` would run.

- The value of `groceryItem` is `'papaya'`, so the third `case` runs— `Papayas are $1.29` is logged to the console.

- The `break` keyword tells the computer to exit the block and not execute any more code or check any other cases inside the code block.
  Note: Without the `break` keyword at the end of each case, the program would execute the code for all matching cases and the default code as well. This behavior is different from `if/else` conditional statements which execute only one block of code.

- At the end of each `switch` statement, there is a `default` statement. If none of the `case`s are true, then the code in the `default` statement will run.
