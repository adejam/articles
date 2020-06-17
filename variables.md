# VARIABLES

A variable is a container for a data which provides a way of labeling data with a descriptive name. Variables label and store data in memory,update information stored in it and Reference or “get” information stored in it.

It is important to distinguish that variables are not values; they contain values and represent them with a name.


## Creating a Variable

### ```var```

 Before the introduction of ES6 version of javascript, Programmers use the ```var``` keyword to create a variable.

 ```
 var myName = 'Arya';
 console.log(myName);// Output: Arya
 ```

### ```let```

 The ```let``` keyword was introduced in ES6. The ```let``` keyword signals that the variable can be reassigned a different value.

 ```
 let meal = 'Enchiladas';
 console.log(meal); // Output: Enchiladas
 meal = 'Burrito';
 console.log(meal); // Output: Burrito
 ```

#### Similarities of ```var``` and ```let``` keywords
- Both can be used to declare a variable without assigning the variable a value. In such a case, the variable will be automatically initialized with a value of ```undefined```:
 ```
 let price;
 console.log(price); // Output: undefined
 price = 350;
 console.log(price); // Output: 350
 ```

 ```
 var price;
 console.log(price); // Output: undefined
 price = 350;
 console.log(price); // Output: 350
 ```
 If we don’t assign a value to a variable declared using the ```let``` keyword, it automatically has a value of undefined.


- From the above similarity, it can be established that the value of both variables can be reassigned.


#### Disimilarities between ```var``` and ```let``` keywords

the difference between them is that ```var``` is function scoped and ```let``` is block scoped. example:

```
console.log(x);
var x=5;
console.log(x); //Output: undefined, 5
```

if an undeclared variable is logged to the console and later declared with ```var``` and assigned a value, it will return undefine and the value assigned to it.

an error will be returned if let is used in declaring such variable. example:


```
console.log(x); // output: ReferenceError: x is not defined
let x=5;
console.log(x); //Output: 5
```

### ```const```

Just like with ```var``` and ```let``` you can store any value in a ```const``` variable. The way you declare a const variable and assign a value to it follows the same structure as ```let``` and ```var```.

```
const myName = 'Gilberto';
console.log(myName); // Output: Gilberto
```

However, a const variable cannot be reassigned because it is constant. If you try to reassign a const variable, you’ll get a TypeError.

Constant variables must be assigned a value when declared. If you try to declare a const variable without a value, you’ll get a SyntaxError.

```
NOTE: ```let``` is the preferred way to declare a variable when it can be reassigned, and ```const``` is the preferred way to declare a variable with a constant value.
```


### General Rules for Naming Variables:

- Variable names cannot start with numbers.

- Variable names are case sensitive, so myName and myname would be different variables. It is bad practice to create two variables that have the same name using different cases.

- Variable names cannot be the same as keywords. For a comprehensive list of keywords check out [MDN’s keyword documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Keywords).



## Mathematical Assignment Operators

Variables and math operators can be used to calculate new values and assign them to a variable.

```
let w = 4;
w = w + 1;

console.log(w); // Output: 5
```

In the example above, a variable ```w``` is created with the number ```4``` assigned to it. The following line, ```w = w + 1```, increases the value of ```w``` from ```4``` to ```5```.

Another way that ```w``` could have been reassigned after performing some mathematical operation on it is to use built-in mathematical assignment operators. We could re-write the code above to be:

```
let w = 4;
w += 1;

console.log(w); // Output: 5
```

In the second example, the ```+=``` assignment operator is used to reassign ```w```. We’re performing the mathematical operation of the first operator ```+``` using the number to the right, then reassigning ```w``` to the computed value.

We also have access to other mathematical assignment operators: ```-=```, ```*=```, and ```/=``` which work in a similar fashion.

```
let x = 20;
x -= 5; // Can be written as x = x - 5
console.log(x); // Output: 15

let y = 50;
y *= 2; // Can be written as y = y * 2
console.log(y); // Output: 100

let z = 8;
z /= 2; // Can be written as z = z / 2
console.log(z); // Output: 4
```

## The Increment and Decrement Operator

The increment operator will increase the value of the variable by 1. The decrement operator will decrease the value of the variable by 1. For example:

```
let a = 10;
a++;
console.log(a); // Output: 11
```

```
let b = 20;
b--;
console.log(b); // Output: 19
```

Just like the previous mathematical assignment operators (```+=```, ```-=```, ```*=```, ```/=```), the variable’s value is updated and assigned as the new value of that variable.

## String Concatenation with Variables

The ```+``` operator can be used to combine two string values even if those values are being stored in variables:

```
let myPet = 'armadillo';
console.log('I own a pet ' + myPet + '.'); // Output: 'I own a pet armadillo.'
```

In the example above, we assigned the value ```'armadillo'``` to the ```myPet``` variable. On the second line, the ```+``` operator is used to combine three strings: ```'I own a pet'```, the value saved to ```myPet```, and ```'.'```. We log the result of this concatenation to the console as:

```
I own a pet armadillo.
```

## String Interpolation(Template Literals)

Variables can be inserted or interpolated into strings using template literals. example:

```
const myPet = 'armadillo';
console.log(`I own a pet ${myPet}.`);// Output: I own a pet armadillo.
```

Notice that:

- a template literal is wrapped by backticks ``` ` ```.
- Inside the template literal, there is a placeholder, ```${myPet}```. The value of ```myPet``` is inserted into the template literal.
- When we interpolate ``` `I own a pet ${myPet}.` ```, the output we print is the string: ```'I own a pet armadillo.'```

One of the biggest benefits to using template literals is the readability of the code. Using template literals, one more easily tell what the new string will be. Also there won't be a need to worry about escaping double quotes or single quotes.

## Typeof Operator

The ```typeof``` operator checks the value to its right and returns, or passes back, a string of the data type. It is used to check the data type of a variable’s value.

```
const unknown1 = 'foo';
console.log(typeof unknown1); // Output: string

const unknown2 = 10;
console.log(typeof unknown2); // Output: number

const unknown3 = true;
console.log(typeof unknown3); // Output: boolean
```

