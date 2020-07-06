# BROWSER COMPATIBILITY AND TRANSPILATION

It is mostly required to update web browser every few months. The reasons include addressing security vulnerabilities, adding features, and supporting new HTML, CSS, and JavaScript syntax.

The reasons above imply there is a period before a software update is released when there are security vulnerabilities and unsupported language syntax.

This article focuses on the latter. Specifically, how developers address the gap between the new JavaScript syntax that they use and the JavaScript syntax that web browsers recognize.

This has become a widespread concern for web developers since Ecma International, the organization responsible for standardizing JavaScript, released a new version of it in 2015, called ECMAScript2015, commonly referred to as ES6. Note, the 6 refers to the version of JavaScript and is not related to the year it was released (the previous version was ES5).

Upon release, web developers quickly adopted the new ES6 syntax, as it improved readability and efficiency. However, ES6 was not supported by most web browsers, so developers ran into browser compatibility issues.

In this article, i will discuss two important tools for addressing browser compatibility issues.

- caniuse.com — A website that provides data on web browser compatibility for HTML, CSS, and JavaScript features. I will discuss how to use it to look up ES6 feature support.

- Babel — A Javascript library that can be used to convert new, unsupported JavaScript (ES6), into an older version (ES5) that is recognized by most modern browsers.

This [cheatsheet](https://www.codecademy.com/learn/introduction-to-javascript/modules/learn-javascript-transpilation/cheatsheet) will explain some concepts mentioned above.

## [caniuse.com](https://caniuse.com/)

Since Ecma’s release of ECMAScript2015 (ES6), software companies have slowly added support for ES6 features and syntax. While most new browser versions support the majority of the ES6 library, there are still a couple sources of compatibility issues:

- Some users have not updated to the latest, ES6 supported web browser version.

- A few ES6 features, like modules, are still not supported by most web browsers.

Because companies add support for ES6 features gradually, it’s important to know how to look up browser support on a feature-by-feature basis. The website [caniuse.com](caniuse.com) is the best resource for finding browser compatibility information.

In caniuse, one can enter an ES6 feature, like let, and see the percentage of browsers that recognize it. One can also see when each major web browser (Chrome, Safari, Edge, etc.) added support for the keyword.


## Why ES6?

Before learning how to set up a JavaScript project that converts ES6 to an older version, it’s worth understanding a few of the reasons Ecma made such substantial updates.

The version of JavaScript that preceded ES6 is called JavaScript ES5. Three reasons for the ES5 to ES6 updates are listed below:

- Readability and economy of code — The new syntax is often easier to understand (more readable) and requires fewer characters to create the same functionality (economy of code).

- Addresses sources of ES5 bugs — Some ES5 syntax led to common bugs. With ES6, Ecma introduced syntax that mitigates some of the most common pitfalls.

- A similarity to other programming languages — JavaScript ES6 is syntactically more similar to other object-oriented programming languages. This leads to less friction when experienced, non-JavaScript developers want to learn JavaScript.

Because ES6 addressed the above issues, Ecma knew that adoption by web developers would occur quickly, while web browser support lagged behind.

To limit the impact of ES6 browser compatibility issues, Ecma made the new syntax backwards compatible, which means one can map JavaScript ES6 code to ES5.

```
var pasta = "Spaghetti"; // ES5 syntax

const meat = "Pancetta"; // ES6 syntax

let sauce = "Eggs and cheese"; // ES6 syntax

// Template literals, like the one below, were introduced in ES6
const carbonara = `You can make carbonara with ${pasta}, ${meat}, and a sauce made with ${sauce}.`;
```
Below is the the ES5 equivalent of the ES6 code above:
```
var pasta = "Spaghetti"; // ES5 syntax

var meat = "Pancetta"; // ES5 syntax

var sauce = "Eggs and cheese"; // ES5 syntax

var carbonara = "You can make carbonara with "+pasta+", "+meat+ ", and a sauce made with "+sauce+".";
```

## Transpilation With Babel

In the last exercise, i manually converted ES6 code to ES5. Although manual conversion only took a few minutes, it is unsustainable as the size of the JavaScript file increases.

Because ES6 is predictably backwards compatible, a collection of JavaScript programmers developed a JavaScript library called Babel that transpiles ES6 JavaScript to ES5.

*Transpilation* is the process of converting one programming language to another.

In the remaining exercises of this lesson, i will discuss how to use Babel to transpile the new, easy-to-write version of JavaScript (ES6) to the old, browser-compatible version of JavaScript (ES5).

In the instructions below, i will pass JavaScript ES6 code to Babel, which will transpile it to ES5 and write it to a file in the lib directory.

1.In the terminal window of the root directory of javascript project file type:

```
npm install babel-cli
```
This installs one of the two required Babel packages.

2.In the terminal window type:
```
npm install babel-preset-env
```

This installs the second of two required Babel packages.

3.In the terminal, type ```npm run build``` and press enter.


## npm init

In the last exercise, i wrote one command in the terminal to transpile ES6 code to ES5. In the next exercises i will discuss how to setup a JavaScript project that transpiles code when i run ```npm run build``` from the root directory of a JavaScript project.

The first step is to place the ES6 JavaScript file in a directory called **src**. From the root directory, the path to the ES6 file is **./src/main.js**

The initial JavaScript project file structure will be:
```
project
|_ src
|___ main.js
```

Before installing Babel, there is need to setup the project to use the [node package manager (npm)](https://docs.npmjs.com/getting-started/what-is-npm). Developers use npm to access and manage Node packages. Node packages are directories that contain JavaScript code written by other developers. One can use these packages to reduce duplication of work and avoid bugs.

Before Babel can be added to the project directory, i need to run ```npm init```. The ```npm init``` command creates a **package.json** file in the root directory.

A **package.json** file contains information about the current JavaScript project. Some of this information includes:

- Metadata — This includes a project title, description, authors, and more.

- A list of node packages required for the project — If another developer wants to run the project, npm looks inside package.json and downloads the packages in this list.

- Key-value pairs for command line scripts — I can use npm to run these shorthand scripts to perform some process. In a later exercise, i will add a script that runs Babel and transpiles ES6 to ES5.
I can create a package.json file by typing ```npm init``` into the terminal.

If a user have Node installed on his computer,The terminal prompts the user to fill in fields for the project’s metadata (name, description, etc.)

The user is not required to answer the prompts, though it is recommend at minimum, the user adds his own title and description. If the user don’t want to fill in a field, he can press enter. npm will leave fill these fields with default values or leave them empty when it creates the package.json file.

After running ```npm init```, the directory structure will contain the following files and folders:

```
project
|_ src
|___ main.js
|_ package.json
```

npm adds the package.json file to the same level as the src directory.

## Install Node Packages

I use the npm ```install``` command to install new Node packages locally. The ```install``` command creates a folder called **node_modules** and copies the package files to it. The install command also installs all of the dependencies for the given package.

To install Babel, i need to npm ```install``` two packages, ```babel-cli``` and ```babel-preset-env```. However, npm installs over one hundred other packages that are dependencies for Babel to run properly.

I install Babel with the following two commands:

```
$ npm install babel-cli -D
$ npm install babel-preset-env -D
```

The ```babel-cli``` package includes command line Babel tools, and the ```babel-preset-env``` package has the code that maps any JavaScript feature, ES6 and above (ES6+), to ES5.

The ```-D``` flag instructs npm to add each package to a property called ```devDependencies``` in **package.json**. Once the project’s dependencies are listed in ```devDependencies```, other developers can run the project without installing each package separately. Instead, they can simply run ```npm install``` — it instructs npm to look inside **package.json** and download all of the packages listed in ```devDependencies```.

Once i ```npm install``` packages, i can find the Babel packages and all their dependencies in the node_modules folder. The new directory structure contains the following:
```
project
|_ node_modules
|___ .bin
|___ ...
|_ src
|___ main.js
|_ package.json
```

The ... in the file structure above is a placeholder for 100+ packages that npm installed.


## .babelrc

After downloading the Babel packages, i need to specify the version of the source JavaScript code.

I can specify the initial JavaScript version inside of a file named **.babelrc**. In the root directory, i can run ```touch .babelrc``` to create this file.

The project directory contains the following folders and files:

```
project
|_ node_modules
|___ .bin
|___ ...
|_ src
|___ main.js
|_ .babelrc
|_ package.json
```

Inside **.babelrc** i need to define the preset for the source JavaScript file. The preset specifies the version of the initial JavaScript file.

Usually, i want to transpile JavaScript code from versions ES6 and later (ES6+) to ES5. From this point on, i will refer to the source code as ES6+, because Ecma introduces new syntax with each new version of JavaScript.

To specify that i am transpiling code from an ES6+ source, i have to add the following JavaScript object into **.babelrc**:

```
{
  "presets": ["env"]
}
```

When i run Babel, it looks in **.babelrc** to determine the version of the initial JavaScript file. In this case, **["env"]** instructs Babel to transpile any code from versions ES6 and later.


## Babel Source Lib

There’s one last step before i can transpile the code. I need to specify a script in **package.json** that initiates the ES6+ to ES5 transpilation.

Inside of the **package.json** file, there is a property named ```"scripts"``` that holds an object for specifying command line shortcuts. It looks like this:

```
...
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1"
}, ...
```

In the code above, the ```"scripts"``` property contains an object with one property called ```"test"```. Below the ```"test"``` property, i will add a script that runs Babel like this:

```
...
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1",
  "build": "babel src -d lib"
}
```

In the ```"scripts"``` object above, i add a property called ```"build"```. The property’s value, "babel src -d lib", is a command line method that transpiles ES6+ code to ES5. Let’s consider each argument in the method call:

- ```babel``` — The Babel command call responsible for transpiling code.

- ```src``` — Instructs Babel to transpile all JavaScript code inside the **src** directory.
- ```d``` — Instructs Babel to write the transpiled code to a directory.
- ```lib``` — Babel writes the transpiled code to a directory called ```lib```.

Next, i’ll run the ```babel src -d lib``` method to transpile the ES6+ code.

## Build

I am ready to transpile the code! In the last exercise, i wrote the following script in **package.json**:
```
"build": "babel src -d lib"
```

Now, i need to call ```"build"``` from the command line to transpile and write ES5 code to a directory called ```lib```.

From the command line, i type:

```
npm run build
```

The command above runs the build script in **package.json**.

Babel writes the ES5 code to a file named main.js (it’s always the same name as the original file), inside of a folder called ```lib```. The resulting directory structure is:

```
project
|_ lib
|___ main.js
|_ node_modules
|___ .bin
|___ ...
|_ src
|___ main.js
|_ .babelrc
|_ package.json
```

Notice, the directory contains a new folder named **lib**, with one file, called **main.js**.

The ```npm run build``` command will transpile all JavaScript files inside of the src folder. This is helpful for larger JavaScript projects — regardless of the number of JavaScript files, i only need to run one command (```npm run build```) to transpile all of the code.
