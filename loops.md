# LOOPS

A loop is a programming tool that repeats a set of instructions until a specified condition, called a stopping condition is reached. Programmers rely on loops all the time!. When referring to loops the generic term iterate is often used; iterate simply means “to repeat”.

When it is needed to reuse a task in a code, the action is often bundled in a function. Similarly, when a process has to be repeated multiple times in a row, it is best to write a loop. Loops allows creation of efficient code that automates processes to make scalable, manageable programs.

![loops](/images/loops.svg)

As illustrated in the diagram, loops iterate or repeat an action until a specific condition is met. When the condition is met, the loop stops and the computer moves on to the next part of the program.


## Repeating Tasks Manually

Before writing loops, taking a moment to develop an appreciation for loops. The best way to do that is by showing how cumbersome it would be if a repeated task required one to type out the same code every single time.

```
vacationSpots = ['jh', 'kjh', 'jkh'];

console.log(vacationSpots[0]);
console.log(vacationSpots[1]);
console.log(vacationSpots[2]);

/*Outputs:
jh
kjh
jkh
*/
```

## The For Loop

Instead of writing out the same code over and over, loops allow computers to repeat a given block of code on its own. One way to give computers these instructions is with a ```for``` loop.

The typical ```for``` loop includes an iterator variable that usually appears in all three expressions. The iterator variable is initialized, checked against the stopping condition, and assigned a new value on each loop iteration. Iterator variables can have any name, but it’s best practice to use a descriptive variable name.

A ```for``` loop contains three expressions separated by ```;``` inside the parentheses:

1. an initialization starts the loop and can also be used to declare the iterator variable.

2. a stopping condition is the condition that the iterator variable is evaluated against— if the condition evaluates to ```true``` the code block will run, and if it evaluates to ```false``` the code will stop.

3. an iteration statement is used to update the iterator variable on each loop.

The ```for``` loop syntax looks like this:

```
for (let counter = 0; counter < 4; counter++) {
  console.log(counter);
}
In this example, the output would be the following:

0
1
2
3
```

Let’s break down the example:

- The initialization is ```let counter = 0```, so the loop will start counting at ```0```.

- The stopping condition is ```counter < 4```, meaning the loop will run as long as the iterator variable, ```counter```, is less than 4.

- The iteration statement is ```counter++```. This means after each loop, the value of ```counter``` will increase by 1. For the first iteration ```counter``` will equal ```0```, for the second iteration ```counter``` will equal 1, and so on.

- The code block is inside of the curly braces, ```console.log(counter)```, will execute until the condition evaluates to ```false```. The condition will be false when ```counter``` is greater than or equal to 4 — the point that the condition becomes false is sometimes called the stop condition.

This ```for``` loop makes it possible to write ```0```, ```1```, ```2```, and ```3``` programmatically.



## Looping in Reverse


What if it is required for the ```for``` loop to log ```3```, ```2```, ```1```, and then ```0```? With simple modifications to the expressions, the loop can be made to run backward!

To run a backward ```for``` loop:

- Set the iterator variable to the highest desired value in the initialization expression.

- Set the stopping condition for when the iterator variable is less than the desired amount.

- The iterator should decrease in intervals after each iteration.

```
// The loop below loops from 0 to 3. Edit it to loop backwards from 3 to 0
for (let counter = 3; counter >= 0; counter--){
  console.log(counter);
}
/* Output:
3
2
1
0
*/
```

## Looping through Arrays

```for``` loops are very handy for iterating over data structures. For example, i can use a ```for``` loop to perform the same operation on each element on an array. Arrays hold lists of data, like customer names or product information. Imagine i owned a store and wanted to increase the price of every product in my catalog. That could be a lot of repeating code, but by using a for loop to iterate through the array i could accomplish this task easily.

To loop through each element in an array, a for loop should use the array’s ```.length``` property in its condition.

Check out the example below to see how for loops iterate on arrays:

```
const animals = ['Grizzly Bear', 'Sloth', 'Sea Lion'];
for (let i = 0; i < animals.length; i++){
  console.log(animals[i]);
}
/*This example would give you the following output:

Grizzly Bear
Sloth
Sea Lion
*/
```


In the loop above, i have named the iterator variable ```i```. This is a variable naming convention is common in a lot of loops. When i use ```i``` to iterate through arrays ```i``` can think of it as being short-hand for the word index. Notice how the stopping condition checks that ```i``` is less than ```animals.length```. Remember that arrays are zero-indexed, the index of the last element of an array is equivalent to the length of that array minus 1. If i tried to access an element at the index of ```animals.length``` i will have gone too far!.

With ```for``` loops, it’s easier to work with elements in arrays.

```
const vacationSpots = ['Bali', 'Paris', 'Tulum'];

// Write your code below
for(let i = 0; i < vacationSpots.length; i++){
  console.log('I would love to visit ' + vacationSpots[i]);
}

/*
I would love to visit Bali
I would love to visit Paris
I would love to visit Tulum
*/
```


## Nested Loops

When there exist a a loop running inside another loop, it is called a nested loop. One use for a nested ```for``` loop is to compare the elements in two arrays. For each round of the outer ```for``` loop, the inner ```for``` loop will run completely.

Let’s look at an example of a nested ```for``` loop:

```
const myArray = [6, 19, 20];
const yourArray = [19, 81, 2];
for (let i = 0; i < myArray.length; i++) {
  for (let j = 0; j < yourArray.length; j++) {
    if (myArray[i] === yourArray[j]) {
      console.log('Both loops have the number: ' + yourArray[j])
    }
  }
};

```


Let’s think about what’s happening in the nested loop in the example. For each element in the outer loop array, ```myArray```, the inner loop will run in its entirety comparing the current element from the outer array, ```myArray[i]```, to each element in the inner array, ```yourArray[j]```. When it finds a match, it prints a string to the console.


```
// Write your code below
const bobsFollowers = ['jdj', 'uyr', 'opk', 'the'];
const tinasFollowers = ['uyr', 'opk', 'kzj'];
const mutualFollowers = [];
for (let i = 0; i < bobsFollowers.length; i++) {
  for (let j = 0; j < tinasFollowers.length; j++) {
    if (bobsFollowers[i] === tinasFollowers[j]) {
      console.log(mutualFollowers.push(tinasFollowers[j]));
    }
  }
};
/*
Output:
1
2
*/
```


## The While Loop

A ```for``` loop can be converted into a ```while``` loop:

```
// A for loop that prints 1, 2, and 3
for (let counterOne = 1; counterOne < 4; counterOne++){
  console.log(counterOne);
}
// A while loop that prints 1, 2, and 3
let counterTwo = 1;
while (counterTwo < 4) {
  console.log(counterTwo);
  counterTwo++;
}
```

Breaking down what’s happening with the ```while``` loop syntax:

- The ```counterTwo``` variable is declared before the loop. I can access it inside the ```while``` loop since it’s in the global scope.

- I start the loop with the keyword ```while``` followed by the stopping condition, or test condition. This will be evaluated before each round of the loop. While the condition evaluates to ```true```, the block will continue to run. Once it evaluates to ```false``` the loop will stop.

- Next, i have the loop’s code block which prints ```counterTwo``` to the console and increments ```counterTwo```.

What would happen if i didn’t increment ```counterTwo``` inside the block? If i didn’t include this, counterTwo would always have its initial value, ```1```. That would mean the testing condition ```counterTwo < 4``` would always evaluate to ```true``` and the loop would never stop running! This is called an infinite loop and it’s something we always want to avoid. Infinite loops can take up all of your computer’s processing power potentially freezing your computer.

So one may be wondering when to use a ```while``` loop! The syntax of a ```for``` loop is ideal when the number of times the loop should run is known, but this is not always known in advance. Think of eating like a ```while``` loop: when one start taking bites, one doesn’t know the exact number one will need to become full. Rather one will eat ```while``` one is hungry. In situations when theres need a loop to execute an undetermined number of times, while loops are the best choice.



## Do...While Statements

In some cases, there will be need to run a piece of code at least once and then loop based on a specific condition after its initial run. This is where the ```do...while``` statement comes in.

A ```do...while``` statement says to do a task once and then keep doing it until a specified condition is no longer met. The syntax for a ```do...while``` statement looks like this:

```
let countString = '';
let i = 0;
do {
  countString = countString + i;
  i++;
} while (i < 5);
console.log(countString);
```

In this example, the code block makes changes to the ```countString``` variable by appending the string form of the ```i``` variable to it. First, the code block after the ```do``` keyword is executed once. Then the condition is evaluated. If the condition evaluates to ```true```, the block will execute again. The looping stops when the condition evaluates to ```false```.

Note that the ```while``` and ```do...while``` loop are different! Unlike the ```while``` loop, ```do...while``` will run at least once whether or not the condition evaluates to ```true```.

```
const firstMessage = 'I will print!';
const secondMessage = 'I will not print!';
// A do while with a stopping condition that evaluates to false
do {
 console.log(firstMessage)
} while (true === false);
// A while loop with a stopping condition that evaluates to false
while (true === false){
  console.log(secondMessage)
};
```


## The break Keyword

Imagine Jamiu looking to adopt a cat. the plan is to go to the shelter every day for a year and then give up. But what if jamiu meet his dream cat on day 65? He doesn’t want to keep going to the shelter for the next 300 days just because his original plan was to go for a whole year. In the code, when i want to stop a loop from continuing to execute even though the original stopping condition i wrote for the loop hasn’t been met, i can use the keyword ```break```.

The ```break``` keyword allows programs to “break” out of the loop from within the loop’s block.

Let’s check out the syntax of a ```break``` keyword:

```
for (let i = 0; i < 99; i++) {
  if (i > 2 ) {
     break;
  }
  console.log('Banana.');
}
console.log('Orange you glad I broke out the loop!');
This is the output for the above code:
/*
Banana.
Banana.
Banana.
Orange you glad I broke out the loop!
*/
```

```break``` statements can be especially helpful when i am looping through large data structures! With breaks, i can add test conditions besides the stopping condition, and exit the loop when they’re met.