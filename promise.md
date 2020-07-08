# JAVASCRIPT PROMISES

Promises are objects that represent the eventual outcome of an asynchronous operation. A ```Promise``` object can be in one of three states:

- **Pending**: The initial state— the operation has not completed yet.

- **Fulfilled**: The operation has completed successfully and the promise now has a *resolved value*. For example, a request’s promise might resolve with a JSON object as its value.

- **Rejected**: The operation has failed and the promise has a reason for the failure. This reason is usually an ```Error``` of some kind.

I refer to a promise as settled if it is no longer pending— it is either fulfilled or rejected. Thinking of a dishwasher as having the states of a promise:

- **Pending**: The dishwasher is running but has not completed the washing cycle.

- **Fulfilled**: The dishwasher has completed the washing cycle and is full of clean dishes.

- **Rejected**: The dishwasher encountered a problem (it didn’t receive soap!) and returns unclean dishes.

If the dishwashing promise is fulfilled, i'll be able to perform related tasks, such as unloading the clean dishes from the dishwasher. If it’s rejected, i can take alternate steps, such as running it again with soap or washing the dishes by hand.

All promises eventually settle, enabling us to write logic for what to do if the promise fulfills or if it rejects.

## Constructing a Promise Object

To create a new ```Promise``` object, the ```new``` keyword and the ```Promise``` constructor method is used:

```
const executorFunction = (resolve, reject) => { };
const myFirstPromise = new Promise(executorFunction);
```

The ```Promise``` constructor method takes a function parameter called the *executor* function which runs automatically when the constructor is called. The executor function generally starts an asynchronous operation and dictates how the promise should be settled.

The executor function has two function parameters, usually referred to as the ```resolve()``` and ```reject()``` functions. The ```resolve()``` and ```reject()``` functions aren’t defined by the programmer. When the ```Promise``` constructor runs, JavaScript will pass **its own** ```resolve()``` and ```reject()``` functions into the executor function.

- ```resolve``` is a function with one argument. Under the hood, if invoked, ```resolve()``` will change the promise’s status from ```pending``` to ```fulfilled```, and the promise’s resolved value will be set to the argument passed into ```resolve()```.

- ```reject``` is a function that takes a reason or error as an argument. Under the hood, if invoked, ```reject()``` will change the promise’s status from ```pending``` to ```rejected```, and the promise’s rejection reason will be set to the argument passed into ```reject()```.

Taking a look at an example executor function in a Promise constructor:

```
const executorFunction = (resolve, reject) => {
  if (someCondition) {
      resolve('I resolved!');
  } else {
      reject('I rejected!');
  }
}
const myFirstPromise = new Promise(executorFunction);
```

Breaking down what’s happening above:

- I declare a variable ```myFirstPromise```

- ```myFirstPromise``` is constructed using ```new Promise()``` which is the ```Promise``` constructor method.

- ```executorFunction()``` is passed to the constructor and has two functions as parameters: ```resolve``` and ```reject```.

- If ```someCondition``` evaluates to ```true```, i invoke ```resolve()``` with the string ```'I resolved!'```

- If not, i invoke ```reject()``` with the string ```'I rejected!'```

In the example, ```myFirstPromise``` resolves or rejects based on a simple condition, but, in practice, promises settle based on the results of asynchronous operations. For example, a database request may fulfill with the data from a query or reject with an error thrown.


## The Node ```setTimeout()``` Function

Knowing how to construct a promise is useful, but most of the time, knowing how to consume, or use, promises will be key. Rather than constructing promises, i’ll be handling ```Promise``` objects returned as the result of an asynchronous operation. These promises will start off pending but settle eventually.

i’ll be simulating this by providing functions that return promises which settle after some time. To accomplish this, i’ll be using ```setTimeout()```. ```setTimeout()``` is a Node API (a comparable API is provided by web browsers) that uses callback functions to schedule tasks to be performed after a delay. ```setTimeout()``` has two parameters: a callback function and a delay in milliseconds.

```
const delayedHello = () => {
  console.log('Hi! This is an asynchronous greeting!');
};

setTimeout(delayedHello, 2000);
```

Here, i invoke ```setTimeout()``` with the callback function ```delayedHello()``` and ```2000```. In at least two seconds ```delayedHello()``` will be invoked. But why is it “at least” two seconds and not exactly two seconds?

This delay is performed asynchronously—the rest of the program won’t stop executing during the delay. Asynchronous JavaScript uses something called the *event-loop*. After two seconds, ```delayedHello()``` is added to a line of code waiting to be run. Before it can run, any synchronous code from the program will run. Next, any code in front of it in the line will run. This means it might be more than two seconds before ```delayedHello()``` is actually executed.

taking a look at how i’ll be using ```setTimeout()``` to construct asynchronous promises:

```
const returnPromiseFunction = () => {
  return new Promise((resolve, reject) => {
    setTimeout(( ) => {resolve('I resolved!')}, 1000);
  });
};

const prom = returnPromiseFunction();
```

In the example code, i invoked ```returnPromiseFunction()``` which returned a promise. I assigned that promise to the variable ```prom```. Similar to the asynchronous promises encountered in production, ```prom``` will initially have a status of pending.

## Consuming Promises

The initial state of an asynchronous promise is ```pending```, but i have a guarantee that it will settle. How do i tell the computer what should happen then? Promise objects come with an aptly named ```.then()``` method. It allows us to say, “I have a promise, when it settles, then here’s what I want to happen…”

In the case of the dishwasher promise, the dishwasher will run ```then```:

- If the promise rejects, this means i have dirty dishes, and i’ll add soap and run the dishwasher again.

- If the promise fulfills, this means i have clean dishes, and i’ll put the dishes away.

```.then()``` is a higher-order function— it takes two callback functions as arguments. I refer to these callbacks as *handlers*. When the promise settles, the appropriate handler will be invoked with that settled value.

- The first handler, sometimes called ```onFulfilled```, is a *success handler*, and it should contain the logic for the promise resolving.

- The second handler, sometimes called ```onRejected```, is a *failure handler*, and it should contain the logic for the promise rejecting.

I can invoke ```.then()``` with one, both, or neither handler! This allows for flexibility, but it can also make for tricky debugging. If the appropriate handler is not provided, instead of throwing an error, ```.then()``` will just return a promise with the same settled value as the promise it was called on. One important feature of ```.then()``` is that it always returns a promise. I’ll return to this in more detail in a later exercise and explore why it’s so important.


## The ```onFulfilled``` and ```onRejected``` Functions

To handle a “successful” promise, or a promise that resolved, i invoke ```.then()``` on the promise, passing in a success handler callback function:

```
const prom = new Promise((resolve, reject) => {
  resolve('Yay!');
});

const handleSuccess = (resolvedValue) => {
  console.log(resolvedValue);
};

prom.then(handleSuccess); // Prints: 'Yay!'
```

Breaking down what’s happening in the example code:

- ```prom``` is a promise which will resolve to ```'Yay!'```.

- I define a function, ```handleSuccess()```, which prints the argument passed to it.

- I invoke ```prom```‘s ```.then()``` function passing in the ```handleSuccess()``` function.

- Since ```prom``` resolves, ```handleSuccess()``` is invoked with ```prom```‘s resolved value, ```'Yay'```, so ```'Yay'``` is logged to the console.

With typical promise consumption, i won’t know whether a promise will resolve or reject, so i’ll need to provide the logic for either case. I can pass both an ```onFulfilled``` and ```onRejected``` callback to ```.then()```.

```
let prom = new Promise((resolve, reject) => {
  let num = Math.random();
  if (num < .5 ){
    resolve('Yay!');
  } else {
    reject('Ohhh noooo!');
  }
});

const handleSuccess = (resolvedValue) => {
  console.log(resolvedValue);
};

const handleFailure = (rejectionReason) => {
  console.log(rejectionReason);
};

prom.then(handleSuccess, handleFailure);
```

Breaking down what’s happening in the example code:

- ```prom``` is a promise which will randomly either resolve with ```'Yay!'``` or reject with ```'Ohhh noooo!'```.

- I pass two handler functions to ```.then()```. The first will be invoked with ```'Yay!'``` if the promise resolves, and the second will be invoked with ```'Ohhh noooo!'``` if the promise rejects.


## Using ```catch()``` with Promises

One way to write cleaner code is to follow a principle called *separation of concerns*. Separation of concerns means organizing code into distinct sections each handling a specific task. It enables us to quickly navigate the code and know where to look if something isn’t working.

Remembering that, ```.then()``` will return a promise with the same settled value as the promise it was called on if no appropriate handler was provided. This implementation allows to separate the resolved logic from the rejected logic. Instead of passing both handlers into one ```.then()```, i can chain a second ```.then()``` with a failure handler to a first ```.then()``` with a success handler and both cases will be handled.

```
prom
  .then((resolvedValue) => {
    console.log(resolvedValue);
  })
  .then(null, (rejectionReason) => {
    console.log(rejectionReason);
  });
```
Since JavaScript doesn’t mind whitespace, it is good to follow a common convention of putting each part of this chain on a new line to make it easier to read. To create even more readable code, i can use a different promise function: ```.catch()```.

The ```.catch()``` function takes only one argument, ```onRejected```. In the case of a rejected promise, this failure handler will be invoked with the reason for rejection. Using ```.catch()``` accomplishes the same thing as using a ```.then()``` with only a failure handler.

Taking a look at an example using ```.catch()```:

```
prom
  .then((resolvedValue) => {
    console.log(resolvedValue);
  })
  .catch((rejectionReason) => {
    console.log(rejectionReason);
  });
```

Breaking down what’s happening in the example code:

- ```prom``` is a promise which randomly either resolves with ```'Yay!'``` or rejects with ```'Ohhh noooo!'```.

- I pass a success handler to ```.then()``` and a failure handler to ```.catch()```.

- If the promise resolves, ```.then()```‘s success handler will be invoked with ```'Yay!'```.

- If the promise rejects, ```.then()``` will return a promise with the same rejection reason as the original promise and ```.catch()```‘s failure handler will be invoked with that rejection reason.


## Chaining Multiple Promises
One common pattern seen with asynchronous programming is multiple operations which depend on each other to execute or that must be executed in a certain order. I might make one request to a database and use the data returned to make another request and so on! Illustrating this with another cleaning example, washing clothes:

I take the dirty clothes and put them in the washing machine. If the clothes are cleaned, **then** i’ll want to put them in the dryer. After the dryer runs, if the clothes are dry, **then** i can fold them and put them away.

This process of chaining promises together is called *composition*. Promises are designed with composition in mind! Here’s a simple promise chain in code:

```
firstPromiseFunction()
.then((firstResolveVal) => {
  return secondPromiseFunction(firstResolveVal);
})
.then((secondResolveVal) => {
  console.log(secondResolveVal);
});
```

Breaking down what’s happening in the example:

- I invoke a function ```firstPromiseFunction()``` which returns a promise.

- I invoke ```.then()``` with an anonymous function as the success handler.

- Inside the success handler i **return** a new promise— the result of invoking a second function, ```secondPromiseFunction()``` with the first promise’s resolved value.

- I invoke a second ```.then()``` to handle the logic for the second promise settling.

- Inside that ```.then()```, i have a success handler which will log the second promise’s resolved value to the console.

In order for the chain to work properly, i had to ```return``` the promise ```secondPromiseFunction(firstResolveVal)```. This ensured that the return value of the first ```.then()``` was the second promise rather than the default return of a new promise with the same settled value as the initial.

## Avoiding Common Mistakes

Promise composition allows for much more readable code than the nested callback syntax that preceded it. However, it can still be easy to make mistakes. In this exercise, i’ll go over two common mistakes with promise composition.

**Mistake 1**: Nesting promises instead of chaining them.

```
returnsFirstPromise()
.then((firstResolveVal) => {
  return returnsSecondValue(firstResolveVal)
    .then((secondResolveVal) => {
      console.log(secondResolveVal);
    })
})
```

Breaking down what’s happening in the above code:

- I invoke ```returnsFirstPromise()``` which returns a promise.

- I invoke ```.then()``` with a success handler.

- Inside the success handler, i invoke ```returnsSecondValue()``` with ```firstResolveVal``` which will return a new promise.

- I invoke a second ```.then()``` to handle the logic for the second promise settling all **inside** the first ```then()```!

- Inside that second ```.then()```, i have a success handler which will log the second promise’s resolved value to the console.

Instead of having a clean chain of promises, i’ve nested the logic for one inside the logic of the other. Imagine if i were handling five or ten promises!

**Mistake 2**: Forgetting to ```return``` a promise.

```
returnsFirstPromise()
.then((firstResolveVal) => {
  returnsSecondValue(firstResolveVal)
})
.then((someVal) => {
  console.log(someVal);
})
```

Breaking down what’s happening in the example:

- I invoke ```returnsFirstPromise()``` which returns a promise.

- I invoke ```.then()``` with a success handler.

- Inside the success handler, i create the second promise, but i forget to ```return``` it!

- I invoke a second ```.then()```. It’s supposed to handle the logic for the second promise, but since i didn’t return, this ```.then()``` is invoked on a promise with the same settled value as the original promise!

Since forgetting to return the promise won’t throw an error, this can be a really tricky thing to debug!

## Using ```Promise.all()```

When done correctly, promise composition is a great way to handle situations where asynchronous operations depend on each other or execution order matters. What if i am dealing with multiple promises, but i don’t care about the order? Think in terms of cleaning again.

For me to consider the house clean, i need my clothes to dry, my trash bins emptied, and the dishwasher to run. I need **all** of these tasks to complete but not in any particular order. Furthermore, since they’re all getting done asynchronously, they should really all be happening at the same time!

To maximize efficiency i should use concurrency, multiple asynchronous operations happening together. With promises, i can do this with the function ```Promise.all()```.

```Promise.all()``` accepts an array of promises as its argument and returns a single promise. That single promise will settle in one of two ways:

- If every promise in the argument array resolves, the single promise returned from ```Promise.all()``` will resolve with an array containing the resolve value from each promise in the argument array.

- If any promise from the argument array rejects, the single promise returned from ```Promise.all()``` will immediately reject with the reason that promise rejected. This behavior is sometimes referred to as failing fast.

Taking a look at a code example:

```
let myPromises = Promise.all([returnsPromOne(), returnsPromTwo(), returnsPromThree()]);

myPromises
  .then((arrayOfValues) => {
    console.log(arrayOfValues);
  })
  .catch((rejectionReason) => {
    console.log(rejectionReason);
  });
```

Breaking down what’s happening:

- I declare ```myPromises``` assigned to invoking ```Promise.all()```.

- I invoke ```Promise.all()``` with an array of three promises— the returned values from functions.

- invoke ```.then()``` with a success handler which will print the array of resolved values if each promise resolves successfully.

- I invoke ```.catch()``` with a failure handler which will print the first rejection message if any promise rejects.

This [cheatsheet](https://www.codecademy.com/learn/introduction-to-javascript/modules/javascript-promises/cheatsheet) can be referred to For a quick review on the concept of promises.

