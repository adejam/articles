# LOOPS

A loop is to interate(repeat) over a set of code until a specified condition is reached.

The article does the following:

- Explain How tasks can be manually repeated
- Explain `For` Loop
- Explain Looping in reverse
- Explain nested loops.
- explain `while` loops.
- Explain `Do...While` statements.
- Explain `break` keyword.

Before we start to work with loops, we will see how cumbersome having to write a repeated task can be:

```js
const myNames = ['Adeleye', 'Oluwaloseyi', 'Jamiu'];

console.log(myNames[0]);
console.log(myNames[1]);
console.log(myNames[2]);

/*Outputs:
Adeleye
Oluwaloseyi
Jamiu
*/
```

The example above might not look so cumbersome as it only involves three values. Imagine we had ove one hundred values. It would be easier to use loops than have to `console.log` each values.

A loop is best used when a process has to be repeated multiple times in a row. Loops allows creation of efficient code that automates processes to make scalable, manageable programs.

## The `For` Loop

Instead of writing out the same code over and over, loops allow computers to repeat a given block of code on its own. One way to give computers these instructions is with a `for` loop.

A `for` loop contains three expressions separated by `;` inside the parentheses:

- An iterator variable is initialized which starts the loop.

- The iterator variable is checked against a stopping condition. If the condition evaluates to `true` the code block will run, and if it evaluates to `false` the code will stop.

- An iteration statement which is used to update the iterator variable on each loop.

Iterator variable can have any name, but it’s best practice to use a descriptive variable name.

from the example above where we munually logged our names we can instead use a `for` loop like below:

```js
const myNames = ['Adeleye', 'Oluwaloseyi', 'Jamiu'];

for (let i = 0; i < myNames.length; i++) {
  console.log(myNames[i]);
}

/*Outputs:
Adeleye
Oluwaloseyi
Jamiu
*/
```

We notice that we get the same output as when we manually repeat the codes. Even if we have over a hundred values for `myNames`, we would only need to write the same line of code.

From the code example above

- The initialization is `let i = 0` and the iterator variable is `i`, so the loop will start counting at `0`.

- The stopping condition is `i < myNames.length`, meaning the loop will run as long as the iterator variable, `i`, is less than the length of `myNames` variable.

- The iteration statement is `i++`. This means that after each loop, the value of `counter` will increase by 1. For the first iteration `i` will equal `0`, for the second iteration `i` will equal 1, and so on.

- The code block is inside of the curly braces, `console.log(myNames[i])`, will execute until the condition evaluates to `false`. The condition will be false when `i` is greater than or equal to `myNames.length`.

## Looping in Reverse

With simple modifications to the expressions, the `for` loop can be made to run backward and display results in reverse.

To run a backward `for` loop:

- Set the iterator variable to the highest desired value in the initialization expression.

- Set the stopping condition for when the iterator variable is less than the desired amount.

- The iterator should decrease in intervals after each iteration.

```js
const myNames = ['Adeleye', 'Oluwaloseyi', 'Jamiu'];

for (let i = myNames.length; i >= 0; i--) {
  console.log(myNames[i]);
}

/*Outputs:
Jamiu
Oluwaloseyi
Adeleye
*/
```

## Nested Loops

Nested is when there exist a loop running inside another loop. This is useful when comparing the elements of two arrays. For each round of the outer `for` loop, the inner `for` loop will run completely.

```js
const firstNumbers = [6, 19, 20];
const secondNumbers = [19, 81, 2];
for (let i = 0; i < firstNumbers.length; i++) {
  for (let j = 0; j < secondNumbers.length; j++) {
    if (firstNumbers[i] === secondNumbers[j]) {
      console.log('Both loops have the number: ' + secondNumbers[j]);
    }
  }
} //OutPuts: Both loops have the number: 19
```

For each element in the outer loop array, `firstNumbers`, the inner loop will run in its entirety comparing the current element from the outer array, `firstNumbers[i]`, to each element in the inner array, `secondNumbers[j]`. When it finds a match, it prints a string to the console.

## The While Loop

A `for` loop can be converted into a `while` loop:

```js
// A for loop that prints 1, 2, and 3
for (let counterOne = 1; counterOne < 4; counterOne++) {
  console.log(counterOne);
}
// A while loop that prints 1, 2, and 3
let counterTwo = 1;
while (counterTwo < 4) {
  console.log(counterTwo);
  counterTwo++;
}
```

Breaking down what’s happening with the `while` loop syntax:

- The `counterTwo` variable is declared before the loop which can be accessed inside the `while` loop since it’s in the global scope.

- We start the loop with the keyword `while` followed by the stopping condition, or test condition. This will be evaluated before each round of the loop. While the condition evaluates to `true`, the block will continue to run. Once it evaluates to `false` the loop will stop.

- Next, we have the loop’s code block which prints `counterTwo` to the console and increments `counterTwo`.

If we didn’t increment counterTwo, it would always have its initial value, `1`. That would mean the testing condition `counterTwo < 4` would always evaluate to `true` and the loop would never stop running(infinite loop). Infinite loops can take up all of our computer’s processing power potentially freezing our computer and it’s something we always want to avoid.

The syntax of a `for` loop is ideal when the number of times the loop should run is known, but this is not always known in advance. While In situations when theres need a loop to execute an undetermined number of times, `while` loops are the best choice.

## `Do...While` Statements

`do...while` statement comes in is a case where there is need to run a piece of code at least once and then loop based on a specific condition after its initial run.

A `do...while` statement says to do a task once and then keep doing it until a specified condition is no longer met.

```js
let countInt = 0;
let i = 0;
do {
  countInt = countInt + i;
  i++;
} while (i < 5);
console.log(countInt);

// Outputs: 10
```

In this example, the code block makes changes to the `countInt` variable by adding `i` variable to it. First, the code block after the `do` keyword is executed once. Then the condition is evaluated. If the condition evaluates to `true`, the block will execute again. The looping stops when the condition evaluates to `false`.

Note that the `while` and `do...while` loop are different. Unlike the `while` loop, `do...while` will run at least once whether or not the condition evaluates to `true`.

```js
const firstChoice = 'Soccer!';
const secondChoice = 'Rugby!';
// A do while with a stopping condition that evaluates to false
do {
  console.log(firstChoice);
} while (true === false);
// A while loop with a stopping condition that evaluates to false
while (true === false) {
  console.log(secondChoice);
}

//Outputs: Soccer!
```

The results only outputs `Soccer!`.

## The break Keyword

The `break` keyword is used to break away from a loop after a certain condition has been met even if the stopping condition has not been met.

The `break` keyword allows programs to _“break”_ out of the loop from within the loop’s block.

```js
for (let i = 0; i < 99; i++) {
  if (i > 2) {
    break;
  }
  console.log('Am still in the loop.');
}
console.log('Glad I broke out the loop!');
// This is the output for the above code:
/*
Am still in the loop.
Am still in the loop.
Am still in the loop.
Glad I broke out the loop!
*/
```

We notice that we were able to break out of the loop even as the stopping condition `i < 99` is still `true`. `break` statements can be especially helpful when looping through large data structures. With `breaks`, we can add test conditions besides the stopping condition, and exit the loop when they’re met.

## For extra reading:

- [W3schools](https://www.w3schools.com/js/js_loop_for.asp)
- [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration)
