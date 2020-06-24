# ARRAYS

Organizing and storing data is a foundational concept of programming.

One way to organize data in real life is by making lists :

```
New Year's Resolutions:
1. Keep a journal
2. Take a falconry class
3. Learn to juggle
```

Writing this list in JavaScript, as an array:

```
let newYearsResolutions = ['Keep a journal', 'Take a falconry class', 'Learn to juggle'];
```
Arrays are JavaScript’s way of making lists. Arrays can store any data types (including strings, numbers, and booleans). Like lists, arrays are ordered, meaning each item has a numbered position.

Here’s an array of the concepts i’ll cover:

## Creating an Array

One way we can create an array is to use an "array literal". An array literal creates an array by wrapping items in square brackets ```[]```. From the previous exercise, arrays can store any data type — i can have an array that holds all the same data types or an array that holds different data types.

![array_literal](/images/array_literal.svg)

Let’s take a closer look at the syntax in the array example:

- The array is represented by the square brackets ```[]``` and the content inside.

- Each content item inside an array is called an element.

- There are three different elements inside the array.

- Each element inside the array is a different data type.

I can also save an array to a variable. It is noticeable that i did this in the previous exercise:
```
let newYearsResolutions = ['Keep a journal', 'Take a falconry class', 'Learn to juggle'];
```


## Accessing Elements

Each element in an array has a numbered position known as its index. We can access individual items using their index, which is similar to referencing an item in a list based on the item’s position.

Arrays in JavaScript are zero-indexed, meaning the positions start counting from ```0``` rather than ```1```. Therefore, the first item in an array will be at position ```0```. Let’s see how we could access an element in an array:

![array_indices](/images/array_indices.svg)

In the code snippet above:

- cities is an array that has three elements.

- I am using bracket notation, ```[]``` with the index after the name of the array to access the element.

- ```cities[0]``` will access the element at index ```0``` in the array ```cities```. ```cities[0]``` can be thought of as accessing the space in memory that holds the string ```'New York'```.

I can also access individual characters in a string using bracket notation and the index. For instance, you can write:

```
const hello = 'Hello World';
console.log(hello[6]);
// Output: W
```
The console will display ```W``` since it is the character that is at index ```6```.


## Update Elements

In the previous exercise, I mentioned how to access elements inside an array or a string by using an index. Once i have access to an element in an array, its value can be updated.

```
let seasons = ['Winter', 'Spring', 'Summer', 'Fall'];

seasons[3] = 'Autumn';
console.log(seasons);
//Output: ['Winter', 'Spring', 'Summer', 'Autumn']
```

In the example above, the ```seasons``` array contained the names of the four seasons.

However, i decided that i preferred to say ```'Autumn'``` instead of ```'Fall'```.

The line, ```seasons[3] = 'Autumn';``` tells our program to change the item at index 3 of the ```seasons``` array to be ```'Autumn'``` instead of what is already there.


## Arrays with let and const

From the previous examples it is noticeable that variables can be declared with both the ```let``` and ```const``` keywords. Variables declared with ```let``` can be reassigned.

Variables declared with the ```const``` keyword cannot be reassigned. However, elements in an array declared with ```const``` remain mutable. Meaning that i can change the contents of a const array, but cannot reassign a new array or a different value.

The instructions below will illustrate this concept more clearly.
```
let condiments = ['Ketchup', 'Mustard', 'Soy Sauce', 'Sriracha'];

const utensils = ['Fork', 'Knife', 'Chopsticks', 'Spork'];

condiments[0] = 'Mayo';
console.log(condiments);

condiments = ['Mayo'];
console.log(condiments);

utensils[3] = 'Spoon';
console.log(utensils);

/*
Output:

[ 'Mayo', 'Mustard', 'Soy Sauce', 'Sriracha' ]
[ 'Mayo' ]
[ 'Fork', 'Knife', 'Chopsticks', 'Spoon' ]
*/
```


## The ```.length``` property

One of an array’s built-in properties is ```length``` and it returns the number of items in the array. I access the ```.length``` property just like i do with strings. Check the example below:

```
const newYearsResolutions = ['Keep a journal', 'Take a falconry class'];

console.log(newYearsResolutions.length);
// Output: 2
```

In the example above, i log ```newYearsResolutions.length``` to the console using the following steps:

- I use dot notation, chaining a period with the property name to the array, to access the ```length``` property of the ```newYearsResolutions``` array.

- Then i log the ```length``` of ```newYearsResolution``` to the console.

- Since ```newYearsResolution``` has two elements, so ```2``` would be logged to the console.

When i want to know how many elements are in an array, i can access the .length property.


## The ```.push()``` Method


There are some built-in JavaScript methods that make working with arrays easier. These methods are specifically called on arrays to make common tasks, like adding and removing elements, more straightforward.

One method, ```.push()``` allows us to add items to the end of an array. Here is an example of how this is used:

```
const itemTracker = ['item 0', 'item 1', 'item 2'];

itemTracker.push('item 3', 'item 4');

console.log(itemTracker);
// Output: ['item 0', 'item 1', 'item 2', 'item 3', 'item 4'];
```

So, how does ```.push()``` work?

- I access the ```push``` method by using dot notation, connecting ```push``` to ```itemTracker``` with a period.

- Then i call it like a function. That’s because ```.push()``` is a function and one that JavaScript allows us to use right on an array.

- ```.push()``` can take a single argument or multiple arguments separated by commas. In this case, i am adding two elements: ```'item 3'``` and ```'item 4'``` to ```itemTracker```.

- Notice that ```.push()``` changes, or mutates, ```itemTracker```. ```.push()``` can also be referred to as a destructive array method since it changes the initial array.


## The ```.pop()``` Method

Another array method, ```.pop()```, removes the last item of an array.

```
const newItemTracker = ['item 0', 'item 1', 'item 2'];

const removed = newItemTracker.pop();

console.log(newItemTracker);
// Output: [ 'item 0', 'item 1' ]
console.log(removed);
// Output: item 2
```

In the example above, calling ```.pop()``` on the ```newItemTracker``` array removed ```item 2``` from the end.

- ```.pop()``` does not take any arguments, it simply removes the last element of ```newItemTracker```.

- ```.pop()``` returns the value of the last element. In the example, i stored the returned value in a variable removed to be used for later.

- ```.pop()``` is a method that mutates the initial array.


## More Array Methods

There are many more array methods than just ```.push()``` and ```.pop()```. All of the array methods that exist on the [Mozilla Developer Network (MDN) array documentation](
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array).

```.pop()``` and ```.push()``` mutate the array on which they’re called. However, there are times that we don’t want to mutate the original array and we can use non-mutating array methods.

Some arrays methods that are available to JavaScript developers include: ```.join()```, ```.slice()```, ```.splice()```, ```.shift()```, ```.unshift()```, and ```.concat()``` amongst many others. Using these built-in methods make it easier to do some common tasks when working with arrays.

Below, i will explore some methods that i have not mentioned yet. I will use these methods to edit a grocery list.

```
const groceryList = ['orange juice', 'bananas', 'coffee beans', 'brown rice', 'pasta', 'coconut oil', 'plantains'];
```
From the example above i can use the following methods:

### ```.shift()``` method

```.shift()``` Remove an item from the beginning of an Array.

```
groceryList.shift();
console.log(groceryList);
/* Outputs: [ 'bananas',
  'coffee beans',
  'brown rice',
  'pasta',
  'coconut oil',
  'plantains' ]
  */
```


### ```.unShift()``` method

```.unShift()``` Add an item to the beginning of an Array.

```
groceryList.unShift('popcorn');
console.log(groceryList);
/* Outputs: [ 'popcorn',
  'bananas',
  'coffee beans',
  'brown rice',
  'pasta',
  'coconut oil',
  'plantains' ]
  */
```


### ```.splice()``` method

```.splice()``` Remove an item by index position.

```
groceryList.splice(pos, 1);
console.log(groceryList);
/* Outputs: ['bananas',
  'coffee beans',
  'brown rice',
  'pasta',
  'coconut oil',
  'plantains' ]
  */
```


### ```.slice()``` method

```.slice()``` Copy an array.

```
groceryList.slice(1,4);
console.log(groceryList);
/* Outputs: [ 'bananas', 'coffee beans', 'brown rice' ]*/
```


### ```.indexOf()``` method

```.indexOf()``` tells the index of an element in an array.

```
groceryList.indexOf('pasta');
console.log(groceryList);
/* Outputs: 4*/
```


## Arrays and Functions

Throughout the lesson i went over arrays being mutable, or changeable. Well what happens if i try to change an array inside a function? Does the array keep the change after the function call or is it scoped to inside the function?

Take a look at the following example where i call ```.push()``` on an array inside a function. Recall, the ```.push()``` method mutates, or changes, an array:

```
const flowers = ['peony', 'daffodil', 'marigold'];

function addFlower(arr) {
  arr.push('lily');
}

addFlower(flowers);

console.log(flowers); // Output: ['peony', 'daffodil', 'marigold', 'lily']
```

Let’s go over what happened in the example:

- The ```flowers``` array that has 3 elements.

- The function ```addFlower()``` has a parameter of ```arr``` uses ```.push()``` to add a ```'lily'``` element into ```arr```.

- I called ```addFlower()``` with an argument of ```flowers``` which will execute the code inside ```addFlower```.

- I checked the value of ```flowers``` and it now includes the ```'lily'``` element! The array was mutated!

So when i pass an array into a function, if the array is mutated inside the function, that change will be maintained outside the function as well. This concept can also be explained as pass-by-reference since what i am actually passing the function is a reference to where the variable memory is stored and changing the memory.


## Nested Arrays

Earlier i mentioned that arrays can store other arrays. When an array contains another array it is known as a nested array. Examine the example below:

```
const nestedArr = [[1], [2, 3]];
```

To access the nested arrays i can use bracket notation with the index value, just like i did to access any other element:

```
const nestedArr = [[1], [2, 3]];

console.log(nestedArr[1]); // Output: [2, 3]
```

Notice that ```nestedArr[1]``` will grab the element in index 1 which is the array ```[2, 3]```. Then, if i wanted to access the elements within the nested array i can chain, or add on, more bracket notation with index values.

```
const nestedArr = [[1], [2, 3]];

console.log(nestedArr[1]); // Output: [2, 3]
console.log(nestedArr[1][0]); // Output: 2
```

In the second ```console.log()``` statement, i have two bracket notations chained to ```nestedArr```. I know that ```nestedArr[1]``` is the array ```[2, 3]```. Then to grab the first element from that array, i use ```nestedArr[1][0]``` and i get the value of ```2```.
