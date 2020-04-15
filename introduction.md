# INTRODUCTION TO JAVASCRIPT

JavaScript is primarily known as the language of most modern web browsers, and its early quirks gave it a bit of a bad reputation. However, the language has continued to evolve and improve. JavaScript is a powerful, flexible, and fast programming language now being used for increasingly complex web development and beyond!

## console

The console is a panel that displays important messages, like errors, for developers. Much of the work the computer does with our code is invisible to us by default. If we want to see things appear on our screen, we can print, or log, to our console directly.

In JavaScript, the ```console``` keyword refers to an object, a collection of data and actions, that we can use in our code. Keywords are words that are built into the JavaScript language, so the computer will recognize them and treats them specially.

One action, or method, that is built into the ```console``` object is the ```.log()``` method. When we write ```console.log()``` what we put inside the parentheses will get printed, or logged, to the console.

```
console.log(5); 
```

This example logs 5 to the console. The semicolon denotes the end of the line, or statement. Although in JavaScript your code will usually run as intended without a semicolon, we recommend learning the habit of ending each statement with a semicolon so you never leave one out in the few instances when they are required. ```console.log()``` can be used to print different types of data.

## Comments

Comments can explain what the code is doing, leave instructions for developers using the code, or add any other useful annotations.

There are two types of code comments in JavaScript:

- A single line comment will comment out a single line and is denoted with two forward slashes ```//``` preceding it.

```
// Prints 5 to the console
console.log(5);
```

Single line comment can also be used to comment after a line of code:

```
console.log(5);  // Prints 5 
```

- A multi-line comment will comment out multiple lines and is denoted with ```/*``` to begin the comment, and ```*/``` to end the comment.

```
/*
This is all commented 
console.log(10);
None of this is going to run!
console.log(99);
*/
```

This syntax can also be used to comment something out in the middle of a line of code:

```
console.log(/*IGNORED!*/ 5);  // Still just prints 5
```

## Data Types

Data types are the classifications we give to the different kinds of data that we use in programming. In JavaScript, there are seven fundamental data types:

- Number: Any number, including numbers with decimals: ```4```, ```8```, ```1516```, ```23.42```.

- String: Any grouping of characters on your keyboard (letters, numbers, spaces, symbols, etc.) surrounded by single quotes: ```' ... '``` or double quotes ```" ... "```. Though we prefer single quotes. Some people like to think of string as a fancy word for text.

- Boolean: This data type only has two possible values— either ```true``` or ```false``` (without quotes). It’s helpful to think of booleans as on and off switches or as the answers to a “yes” or “no” question.

- Null: This data type represents the intentional absence of a value, and is represented by the keyword ```null``` (without quotes).

- Undefined: This data type is denoted by the keyword ```undefined``` (without quotes). It also represents the absence of a value though it has a different use than ```null```.

- Symbol: A newer feature to the language, symbols are unique identifiers, useful in more complex coding.

- Object: Collections of related data.


The first 6 of those types are considered primitive data types. They are the most basic data types in the language. Objects are more complex.


## Arithmetic Operators

An operator is a character that performs a task in our code. JavaScript has several built-in in arithmetic operators, that allow us to perform mathematical calculations on numbers. These include the following operators and their corresponding symbols:

- Add: ```+```

- Subtract: ```-```

- Multiply: ```*```

- Divide: ```/```

- Remainder: ```%```


```
console.log(3 + 4); // Prints 7
console.log(5 - 1); // Prints 4
console.log(4 * 2); // Prints 8
console.log(9 / 3); // Prints 3
console.log(11 % 3); // Prints 2
```

The remainder operator, sometimes called modulo, returns the number that remains after the right-hand number divides into the left-hand number as many times as it evenly can: 11 % 3 equals 2 because 3 fits into 11 three times, leaving 2 as the remainder.


## String Concatenation

The process of appending one string to another is called concatenation. 

```
console.log('hi' + 'ya'); // Prints 'hiya'
console.log('wo' + 'ah'); // Prints 'woah'
console.log('I love to ' + 'code.') // Prints 'I love to code.'
```

Just like with regular math, we can combine, or chain, our operations to get a final result:

```
console.log('One' + ', ' + 'two' + ', ' + 'three!'); // Prints 'One, two, three!'
```

## Properties

Properties are used to check informations on a data type.

Every string instance has a property called ```length``` that stores the number of characters in that string. You can retrieve property information by appending the string with a period and the property name:

```
console.log('Teaching the world how to code'.length); // prints 30
```

The ```.``` is another operator! We call it the dot operator.

In the example above, the value saved to the ```length``` property is retrieved from the instance of the string, ```'Teaching the world how to code'```. The program prints 30 to the console, because ```'Teaching the world how to code'``` has thirty characters in it.

## Methods 

Methods are actions we can perform. JavaScript provides a number of string methods.

these methods are called, or used  by appending an instance with a period (the dot operator), the name of the method, and opening and closing parentheses: e.g. ```'example string'.methodName()```.

When we use ```console.log()``` we’re calling the ```.log()``` method on the ```console``` object.

Some methods are explained below:

- ```.toUpperCase()``` method: This method returns a string in all capital letters.

```
console.log('hello'.toUpperCase()); // Prints 'HELLO'
```
 ```.toUpperCase()``` method is called on the string instance 'hello'. The result is logged to the console. This method returns a string in all capital letters: 'HELLO'.

- ```.startsWith()``` method:

  This method takes in an argument as checks if the string to which it is appended starts with that argument. If it starts with the argument then it prints ```true``` and if it does not start with the argument it prints ```false```.

```
console.log('Hey'.startsWith('H')); // Prints true
```

the ```.startsWith()``` method is called on the string instance ```'Hey```'. This method also accepts the character ```'H'``` as an input, or argument, between the parentheses. Since the string ```'Hey'``` does start with the letter ```'H'```, the method returns the boolean ```true```.


- ```.trim()``` method
 The ```.trim()``` method is used to remove white spaces at the beginning and end of a string.

 ```
console.log('    Remove whitespace   '.trim());
 ``` 

check the list of built-in string methods in the [JavaScript documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String).


## Built-in Objects

In addition to console, there are other [objects built into JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects). These objects have methods.
For example, the built-in ```Math``` object in javascript is used to to perform more complex mathematical operations than arithmetic. Let’s call the .random() method from the built-in Math object:

```
console.log(Math.random()); // Prints a random number between 0 and 1
```

In the example above, we called the ```.random()``` method by appending the object name with the dot operator, the name of the method, and opening and closing parentheses. This method returns a random number between 0 and 1.

To generate a random number between 0 and 50, we could multiply this result by 50, like so:

```
Math.random() * 50;
```
The example above will likely evaluate to a decimal. To ensure the answer is a whole number, we can take advantage of another useful Math method called ```Math.floor()```.

```Math.floor()``` takes a decimal number, and rounds down to the nearest whole number. You can use ```Math.floor()``` to round down a random number like this:

```
Math.floor(Math.random() * 50);
```

```Math.ceil()``` takes a decimal number, and rounds up to the nearest whole number. You can use ```Math.ceil()``` to round up a random number like this:

```
Math.ceil(Math.random() * 50);
```

To see all of the properties and methods on the Math object, take a look at [the documentation here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math).














