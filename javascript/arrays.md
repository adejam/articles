# ARRAYS

Arrays are used to store multiple values in a single variable. Arrays can store any data types (including strings, numbers, and booleans). Arrays are ordered, meaning each item has a numbered position.

The article does the following:

- Explain how to create an array
- Explain how to access array elements
- Explain how to update array elements
- Explain arrays with `let` and `const`
- Explain array methods like `.length`, `.push`, `.pop`, `.slice` etc.
- Explain arrays and functions.
- Explain nested arrays.

## Creating an Array

One way we can create an array is to use an "array literal". An array literal creates an array by wrapping items in square brackets `[]`.

```js
const programmingLanguages = ['Javascript', 'PHP', 'Python'];
```

From the above

- The array is represented by the square brackets `[]` and the content inside.

- Each content item inside an array is called an element.

Another way to create an Array is by using the `Array` keyword.

```js
var courses = new Array('Computer science', 'biology', 'physics');
```

Using typeof we can see that an array is an object

```js
const programmingLanguages = ['Javascript', 'PHP', 'Python'];
var courses = new Array('Computer science', 'biology', 'physics');

console.log(typeof programmingLanguages); // Output: object
console.log(typeof courses); // Output: object
```

## Accessing Elements

Each element in an array has a numbered position known as its index. We can access individual items using their index, which is similar to referencing an item in a list based on the item’s position.

Arrays are ordered, meaning each item has a numbered position known as its index. Arrays in JavaScript are zero-indexed, meaning the positions start counting from `0` rather than `1`. Therefore, the first item in an array will be at position `0`.

```js
const programmingLanguages = ['Javascript', 'PHP', 'Python'];
console.log(programmingLanguages[1]); // outputs: PHP
```

from the code above we use the bracket notation, `[]` with the index after the name of the array to access the element.
`programmingLanguages[1]` will access the element at index `1` in the array `programmingLanguages` which points to `PHP`. `programmingLanguages[1]` can be thought of as accessing the space in memory that holds the string `'PHP'`.

We can also access individual characters in a string using bracket notation and the index. For instance, We can write:

```js
const accessMe = 'Access a Letter';
console.log(accessMe[9]);
// Output: L
```

The console will display `L` since it is the character that is at index `9`.

## Update Elements

The value of an array element can be updated Once we have access to the element in an array.

```js
let programmingLanguages = ['Javascript', 'PHP', 'Python'];

programmingLanguages[2] = 'Java';
console.log(programmingLanguages);
//Output: ['Javascript', 'PHP', 'Java']
```

In the example above, the `programmingLanguages` array contained three programming languages.

The line, `programmingLanguages[2] = 'Java';` tells our program to change the item at index 2 of the `programmingLanguages` array to be `'Java'` instead of `'Python'`.

## Arrays with let and const

Conventionally variables can be declared with both the `let` and `const` keywords. Variables declared with `let` can be reassigned while Variables declared with the `const` keyword cannot be reassigned. However, elements in an array declared with `const` can be mutated. Meaning that we can change the contents of a `const` array, but **cannot reassign a new array or a different value**.

The code below illustrates this concept more clearly.

```js
let programmingLanguages = ['Javascript', 'PHP', 'Python'];

const frameworks = ['React', 'Laravel', 'Django'];

programmingLanguages[0] = 'ES6';
console.log(programmingLanguages); // Outputs: ['ES6', 'PHP', 'Python']

programmingLanguages = ['Java'];
console.log(programmingLanguages); // Outputs: ['Java']

frameworks[0] = 'Vue';
console.log(frameworks); // outputs: ['vue', 'Laravel', 'Django'];

frameworks = ['Angular'];
console.log(frameworks); // Outputs: Uncaught TypeError: Assignment to constant variable.
```

We can see that when we assigned a different array to the `programmingLanguages` array declared with the `let` keyword it worked but throws an error when we assigned another array to the `frameworks` array declared with the `const` keyword.

## Array Methods

Some built-in JavaScript methods make working with arrays easier. These methods are specifically called on arrays to make common tasks, like adding and removing elements, more straightforward.

Below are some array methods in Javascript.

### The `.length` property

One of an array’s built-in properties is `length` which returns the number of items in the array. We access the `.length` property just like we do with strings.

```js
const frameworks = ['React', 'Laravel', 'Django'];

console.log(frameworks.length); // Output: 3
```

In the code above, we use dot notation, chaining a period with the property name to the array, to access the `length` property of the `frameworks` array which when logged outputs `3`.

When we want to know how many elements are in an array, we can access the `.length` property.

### The `.push()` Method

One method, `.push()` allows us to add items to the end of an array. Here is an example of how this is used:

```js
const frameworks = ['Vue', 'React', 'Angular'];

frameworks.push('Laravel', 'Django');

console.log(frameworks);
// Output: ['Vue', 'React', 'Angular', 'Laravel', 'Django'];
```

From the code above

- We access the `push` method by using dot notation, connecting `push` to `frameworks` with a period.

- Then we call it like a function. That’s because `.push()` is a function and one that JavaScript allows us to use right on an array.

- `.push()` can take a single argument or multiple arguments separated by commas. In this case, we added two elements: `'Laravel'` and `'Django'` to `frameworks`.

- `.push()` changes, or mutates, `frameworks`. `.push()` can also be referred to as a destructive array method since it changes the initial array.

### The `.pop()` Method

`.pop()`, removes the last item of an array.

```Js
const frameworks = ['Vue', 'React', 'Angular'];

const removedFrameworks = frameworks.pop();

console.log(frameworks); // Output: ['Vue', 'React']

console.log(removedFrameworks);// Output: 'Angular'
```

In the code above, calling `.pop()` on the `frameworks` array removed `Angular` from the end.

`.pop()` does not take any arguments, it simply removes the last element of an array.

`.pop()` returns the value of the last element. In the example, we stored the returned value in a variable `removedFrameworks` which can be used later on.

`.pop()` is a method that mutates the initial array.

## More Array Methods

More arrays methods that are available in JavaScript include: `.join()`, `.slice()`, `.splice()`, `.shift()`, `.unshift()`, and `.concat()` amongst many others. Using these built-in methods make it easier to do some common tasks when working with arrays.

Below, we will explore more methods. We will use these methods to edit a `soccerPlayers` list.

```js
const soccerPlayers = ['Messi', 'Ronaldo', 'De-bruyne', 'Neymar', 'Mbappe', 'Lewandowski'];
```

From the example above we can use the following methods:

### `.shift()` method

`.shift()` removes an item from the beginning of an Array.

```js
soccerPlayers.shift();
console.log(soccerPlayers); // Outputs: ['Ronaldo', 'De-bruyne', 'Neymar', 'Mbappe', 'Lewandowski'];
```

### `.unShift()` method

`.unShift()` Add an item to the beginning of an Array.

```js
soccerPlayers.unshift('Haaland');
console.log(soccerPlayers); // Outputs: ['Haaland', 'Messi', 'Ronaldo', 'De-bruyne', 'Neymar', 'Mbappe', 'Lewandowski'];
```

### `.splice()` method

`.splice()` method can be used to add new elements to an array by an index position and also remove elements from an array by an index position.

Below is an example of how we can use it to add new elements by index position.

```js
soccerPlayers.splice(2, 0, 'Xavi', 'Iniesta');
console.log(soccerPlayers); // Outputs: ['Messi', 'Ronaldo', 'Xavi', 'Iniesta', 'De-bruyne', 'Neymar', 'Mbappe', 'Lewandowski'];
```

- The first parameter `2` defines the position where new elements should be added (spliced in) and the position where the item(s) should be removed.

- The second parameter `0` defines how many elements should be removed in our case no item was removed

We can also use `.splice()` to remove elements from an array by an index position without having to add new elements to the array

```js
soccerPlayers.splice(2, 1);
console.log(soccerPlayers); // Outputs: ['Messi', 'Ronaldo', 'Neymar', 'Mbappe', 'Lewandowski'];
```

### `.slice()` method

`.slice()` slices out a piece of an array into a new array.

```js
const slicedPlayers = soccerPlayers.slice(1, 4);
console.log(slicedPlayers); // Outputs: ["Ronaldo", "De-bruyne", "Neymar"]
```

The `slice()` method takes two arguments like `.slice(1,4)`.

The method then selects elements from the start argument, and up to (but not including) the end argument.

### `.indexOf()` method

`.indexOf()` tells the index of an element in an array.

```js
const neymarIndex = soccerPlayers.indexOf('Neymar');
console.log(neymarIndex); //Outputs: 3
```

There are many more array methods than just the ones mentioned above. We can check for more array methods on the [Mozilla Developer Network (MDN) array documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array).

## Arrays and Functions

Arrays can also be mutated inside a function and keep the change after the function call.

Taking a look at the following example where we call `.push()` on an array inside a function. We know that `.push()` method mutates, or changes, an array:

```js
const soccerPlayers = ['Messi', 'Ronaldo', 'De-bruyne', 'Neymar', 'Mbappe', 'Lewandowski'];
function addPlayer(arr) {
  arr.push('Xavi');
}

addPlayer(soccerPlayers);

console.log(soccerPlayers); // Output: ["Messi", "Ronaldo", "De-bruyne", "Neymar", "Mbappe", "Lewandowski", "Xavi"]
```

From the code snippets above:

- The function `addPlayer()` has a parameter of `arr` and uses `.push()` to add a `'Xavi'` element into `arr`.

- We called `addplayer()` with an argument of `soccerPlayers` which will execute the code inside `addPlayer`.

- We checked the value of `soccerPlayers` and it now includes the `'Xavi'` element! The array was mutated!

So when we pass an array into a function, if the array is mutated inside the function, that change will be maintained outside the function as well. This concept can also be explained as pass-by-reference since we are passing the function as a reference to where the variable memory is stored and changing the memory.

## Nested Arrays

When an array contains another array it is known as a nested array or **Two-dimensional** array. Examine the example below:

```js
const nestedplayers = [['Messi'], ['Ronaldo', 'Neymar']];
```

To access the nested arrays we can use bracket notation with the index value, just like we did to access any other element:

```js
const nestedplayers = [['Messi'], ['Ronaldo', 'Neymar']];

console.log(nestedplayers[1]); // Output: ['Ronaldo', 'Neymar']
```

Notice that `nestedplayers[1]` will grab the element in index 1 which is the array `['Ronaldo', 'Neymar']`. Then, if we wanted to access the elements within the nested array we can chain, or add on, more bracket notation with index values.

```js
const nestedplayers = [['Messi'], ['Ronaldo', 'Neymar']];

console.log(nestedplayers[0]); // Output: ['Messi']
console.log(nestedplayers[1]); // Output: ['Ronaldo', 'Neymar']
console.log(nestedplayers[1][0]); // Output: 'Ronaldo'
```

In the third `console.log()` statement, we have two bracket notations chained to `nestedplayers`. We know that `nestedplayers[1]` is the array `['Ronaldo', 'Neymar']`. Then to grab the first element from that array, we used `nestedplayers[1][0]` and we get `Ronaldo`.

## For more reading

[w3schools Javascript arrays](https://www.w3schools.com/js/js_arrays.asp)
[w3schools Javascript arrays methods](https://www.w3schools.com/js/js_array_methods.asp)
[MDN Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
