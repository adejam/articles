# HIGHER-ORDER FUNCTIONS

Higher-order functions are functions that accept other functions as arguments and/or return functions as output.

Humans are often unaware of the number of assumptions they make when they communicate with one another in their native languages. If someone is told to “count to three,” He would be expected to say or think the numbers one, two and three. It is assumed he would know to start with “one” and end with “three”. With programming, programmers are faced with needing to be more explicit with their directions to the computer. Here’s how i might tell the computer to “count to three”:


```
for (let i = 1; i<=3; i++) {
  console.log(i)
}
```

When humans speak to one another, they share a vocabulary that gives them quick ways to communicate complicated concepts.
When someone say “bake”, it calls to mind a familiar subroutine— preheating an oven, putting something into an oven for a set amount of time, and finally removing it. This allows to abstract away a lot of the details and communicate key concepts more concisely. Instead of listing all those details, one can say, “We baked a cake,” and still impart all that meaning.

In programming, “Abstraction” can be accomplished by writing functions. In addition to allowing reuse of code, functions help to make clear, readable programs. If a programmer encountered ```countToThree()``` in a program, one might be able to quickly guess what the function did without having to stop and read the function’s body.

A level of abstraction can be added to programming through "higher-order functions".  This enables building abstractions on other abstractions, just like “We hosted a birthday party” is an abstraction that may build on the abstraction “We made a cake.”

In summary, using more abstraction in code allows writing more modular code which is easier to read and debug.

## Functions as Data

JavaScript functions behave like any other data type in the language; functions can be assigned to variables, and can then be reassign to new variables.

Below, is an annoyingly long function name that hurts the readability of any code in which it’s used. Let’s pretend this function does important work and needs to be called repeatedly!

```
const announceThatIAmDoingImportantWork = () => {
    console.log("I’m doing very important work!");
};
```


What if this function is to be renamed without sacrificing the source code? the function can be re-assigned to a variable with a suitably short name:

```
const busy = announceThatIAmDoingImportantWork;

busy(); // This function call barely takes any space!
```


```busy``` is a variable that holds a reference to the original function. If the address in memory of ```busy``` cuold be looked up and the address in memory of ```announceThatIAmDoingImportantWork``` they would point to the same place. The new ```busy()``` function can be invoked with parentheses as if that was the name originally given to the function.

I assigned ```announceThatIAmDoingImportantWork``` without parentheses as the value to the ```busy``` variable. The value of the function itself is to be assigned, not the value it returns when invoked.

In JavaScript, functions are first class objects. This means that, like other objects encountered, JavaScript functions can have properties and methods.

Since functions are a type of object, they have properties such as ```.length``` and ```.name``` and methods such as ```.toString()```.More about the methods and properties of functions can be seen in the [documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function).

Functions are special because they can be invoked, but they can still treated like any other type of data.

```
const checkThatTwoPlusTwoEqualsFourAMillionTimes = () => {
  for(let i = 1; i <= 1000000; i++) {
    if ( (2 + 2) != 4) {
      console.log('Something has gone very wrong :( ');
    }
  }
};


const is2p2 = checkThatTwoPlusTwoEqualsFourAMillionTimes;

is2p2();

console.log(is2p2.name);
// Output: checkThatTwoPlusTwoEqualsFourAMillionTimes
```

- The example above is a function ```checkThatTwoPlusTwoEqualsFourAMillionTimes``` which is used to check if "2 + 2 = 4" a million times.

- ```checkThatTwoPlusTwoEqualsFourAMillionTimes``` is then re-assigned to ```is2p2```.

- ```is2p2``` is then evoked.

- ```is2p2``` is then logged with the ```.name``` property to check the real name of the function.


## Functions as Parameters

Since functions can behave like any other type of data in JavaScript, it might not surprise to learn that functions can also pass (into other functions) as parameters. A higher-order function is a function that either accepts functions as parameters, returns a function, or both! We call the functions that get passed in as parameters and invoked callback functions because they get called during the execution of the higher-order function.

When a function is passed in as an argument to another function, it should not br invoked. Invoking the function would evaluate to the return value of that function call. With callbacks, the function itself is passed by typing the function name without the parentheses (that would evaluate to the result of calling the function):

```
const timeFuncRuntime = funcParameter => {
   let t1 = Date.now();
   funcParameter();
   let t2 = Date.now();
   return t2 - t1;
}

const addOneToOne = () => 1 + 1;

timeFuncRuntime(addOneToOne);
```

I wrote a higher-order function, ```timeFuncRuntime()```. It takes in a function as an argument, saves a starting time, invokes the callback function, records the time after the function was called, and returns the time the function took to run by subtracting the starting time from the ending time.

This higher-order function could be used with any callback function which makes it a potentially powerful piece of code.

I then invoked ```timeFuncRuntime()``` first with the ```addOneToOne()``` function - note how i passed in ```addOneToOne``` and did not invoke it.

```
timeFuncRuntime(() => {
  for (let i = 10; i>0; i--){
    console.log(i);
  }
});
```

In this example, i invoked ```timeFuncRuntime()``` with an anonymous function that counts backwards from 10. Anonymous functions can be arguments too.

