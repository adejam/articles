# CLASSES

Classes are a tool that developers use to quickly produce similar objects.
Take, for example, an object representing a dog named ```halley```. This dog’s ```name``` (a key) is ```"Halley"``` (a value) and has an ```age``` (another key) of ```3``` (another value). I create the ```halley``` object below:

```
let halley = {
  _name: 'Halley',
  _behavior: 0,

  get name() {
    return this._name;
  },

  get behavior() {
    return this._behavior;
  },

  incrementBehavior() {
    this._behavior++;
  }
}
```

Say,i own a dog daycare and want to create a catalog of all the dogs who belong to the daycare. Instead of using the syntax above for every dog that joins the daycare, i can create a ```Dog``` class that serves as a template for creating new ```Dog``` objects. For each new dog, i can provide a value for their name.

Classes are a great way to reduce duplicate code and debugging time.

```
class Dog {
  constructor(name) {
    this._name = name;
    this._behavior = 0;
  }

  get name() {
    return this._name;
  }
  get behavior() {
    return this._behavior;
  }

  incrementBehavior() {
    this._behavior ++;
  }
}

const halley = new Dog('Halley');
console.log(halley.name); // Print name value to console
console.log(halley.behavior); // Print behavior value to console
halley.incrementBehavior(); // Add one to behavior
console.log(halley.name); // Print name value to console
console.log(halley.behavior); // Print behavior value to console
```

## Constructor

In the last exercise, you created a class called ```Dog```, and used it to produce a ```Dog``` object.

Although some similarities may be seen between class and object syntax, there is one important method that sets them apart. It’s called the **constructor** method. JavaScript calls the ```constructor()``` method every time it creates a new instance of a class.

```
class Dog {
  constructor(name) {
    this.name = name;
    this.behavior = 0;
  }
}
```

- ```Dog``` is the name of the class. By convention, class names are to be capitalized and CamelCased.

- JavaScript will invoke the ```constructor()``` method every time i create a new instance of the ```Dog``` class.

- This ```constructor()``` method accepts one argument, ```name```.

- Inside of the ```constructor()``` method, i use the ```this``` keyword. In the context of a class, ```this``` refers to an instance of that class. In the ```Dog``` class, i use this to set the value of the Dog instance’s ```name``` property to the ```name``` argument.

- Under ```this.name```, i create a property called ```behavior```, which will keep track of the number of times a dog misbehaves. The ```behavior``` property is always initialized to zero.


## Instances

An instance is an object that contains the property names and methods of a class, but with unique property values. taking a look at the ```Dog``` class example.

```
class Dog {
  constructor(name) {
    this.name = name;
    this.behavior = 0;
  }
}

const halley = new Dog('Halley'); // Create new Dog instance
console.log(halley.name); // Log the name value saved to halley
// Output: 'Halley'
```

Below the Dog class, i use the ```new``` keyword to create an instance of the Dog class. Considering the line of code step-by-step.

- I created a new variable named ```halley``` that will store an instance of the ```Dog``` class.

- I use the ```new``` keyword to generate a new instance of the ```Dog``` class. The new keyword calls the ```constructor()```, runs the code inside of it, and then returns the new instance.

- I pass the ```'Halley'``` string to the ```Dog``` constructor, which sets the ```name``` property to ```'Halley'```.

Finally, i log the value saved to the ```name``` key in the ```halley``` object, which logs ```'Halley'``` to the console.


## Methods

At this point, i have a ```Dog``` class that spins up objects with ```name``` and ```behavior``` properties. Below, i will add getters and a method to bring the class to life.

Class method and getter syntax is the same as it is for objects except commas cannot be included between methods.

```
class Dog {
  constructor(name) {
    this._name = name;
    this._behavior = 0;
  }

  get name() {
    return this._name;
  }

  get behavior() {
    return this._behavior;
  }

  incrementBehavior() {
    this._behavior++;
  }
}
```


In the example above, i add getter methods for ```name``` and ```behavior```. I also prepended the property names with underscores (```_name``` and ```_behavior```), which indicate these properties should not be accessed directly. Under the getters, i add a method named ```.incrementBehavior()```. When i call ```.incrementBehavior()``` on a ```Dog``` instance, it adds 1 to the ```_behavior``` property. Between each of the methods, i did not include commas.


### Method Calls

using the new methods to access and manipulate data from ```Dog``` instances.

```
class Dog {
  constructor(name) {
    this._name = name;
    this._behavior = 0;
  }

  get name() {
    return this._name;
  }

  get behavior() {
    return this._behavior;
  }

  incrementBehavior() {
    this._behavior++;
  }
}

const halley = new Dog('Halley');

```

In the example above, i create the ```Dog``` class, then create an instance, and save it to a variable named ```halley```.

The syntax for calling methods and getters on an instance is the same as calling them on an object — append the instance with a period, then the property or method name. For methods, one must also include opening and closing parentheses.

Creating two ```Dog``` instances and calling the ```.incrementBehavior()``` method on one of them.

```
let nikko = new Dog('Nikko'); // Create dog named Nikko
nikko.incrementBehavior(); // Add 1 to nikko instance's behavior
let bradford = new Dog('Bradford'); // Create dog name Bradford
console.log(nikko.behavior); // Logs 1 to the console
console.log(bradford.behavior); // Logs 0 to the console
```

In the example above, i created two new ```Dog``` instances, ```nikko``` and ```bradford```. Because i increment the behavior of the ```nikko``` instance, but not ```bradford```, accessing ```nikko.behavior``` returns ```1``` and accessing ```bradford.behavior``` returns ```0```.


## Inheritance

Imagine my doggy daycare is so successful that i decide to expand the business and open a kitty daycare. Before the daycare opens, i need to create a ```Cat``` class so i can quickly generate ```Cat``` instances. I know that the properties in the ```Cat``` class (```name```, ```behavior```) are similar to the properties in the ```Dog``` class, though, there will be some differences, because of course, cats are not dogs.

Assuming the Cat class looks like this:

```
class Cat {
  constructor(name, usesLitter) {
    this._name = name;
    this._usesLitter = usesLitter;
    this._behavior = 0;
  }

  get name() {
    return this._name;
  }

  get usesLitter() {
    return this._usesLitter;
  }

  get behavior() {
    return this._behavior;
  }

  incrementBehavior() {
    this._behavior++;
  }
}
```

In the example above, i created a ```Cat``` class. It shares a couple of properties (```_name``` and ```_behavior```) and a method (```.incrementBehavior()```) with the ```Dog``` class from earlier exercises. The ```Cat``` class also contains one additional property (```_usesLitter```), that holds a boolean value to indicate whether a cat can use their litter box.

When multiple classes share properties or methods, they become candidates for inheritance — a tool developers use to decrease the amount of code they need to write.

With inheritance, i can create a parent class (also known as a superclass) with properties and methods that multiple child classes (also known as subclasses) share. The child classes inherit the properties and methods from their parent class.

Abstracting the shared properties and methods from the ```Cat``` and ```Dog``` classes into a parent class called ```Animal```.

```
class Animal {
  constructor(name) {
    this._name = name;
    this._behavior = 0;
  }

  get name() {
    return this._name;
  }

  get behavior() {
    return this._behavior;
  }

  incrementBehavior() {
    this._behavior++;
  }
}
```

In the example above, the ```Animal``` class contains the properties and methods that the ```Cat``` and ```Dog``` classes share (```name```, ```behavior```, ```.incrementBehavior()```).

The diagram below shows the relationships i want to create between the ```Animal```, ```Cat```, and ```Dog``` classes.

![inheritance_diagram](/images/inheritance_diagram.svg)

The code below shows the ```Cat``` class that will inherit information from the ```Animal``` class.

```
class Cat {
  constructor(name, usesLitter) {
    this._name = name;
    this._usesLitter = usesLitter;
    this._behavior = 0;
  }

  get name() {
    return this._name;
  }

  get behavior() {
    return this._behavior;
  }

  get usesLitter() {
    return this._usesLitter;
  }

  incrementBehavior() {
    this._behavior++;
  }
}
```

Now that i have these shared properties and methods in the parent ```Animal``` class, i can extend them to the subclass, ```Cat```.

```
class Cat extends Animal {
  constructor(name, usesLitter) {
    super(name);
    this._usesLitter = usesLitter;
  }
}
```

In the example above, i create a new class named ```Cat``` that extends the ```Animal``` class. Paying special attention to the new keywords: ```extends``` and ```super```.

- The ```extends``` keyword makes the methods of the animal class available inside the cat class.

- The constructor, called when i create a new ```Cat``` object, accepts two arguments, ```name``` and ```usesLitter```.

- The ```super``` keyword calls the constructor of the parent class. In this case, ```super(name)``` passes the name argument of the ```Cat``` class to the constructor of the ```Animal``` class. When the ```Animal``` constructor runs, it sets ```this._name = name;``` for new ```Cat``` instances.

- ```_usesLitter``` is a new property that is unique to the ```Cat``` class, so i set it in the ```Cat``` constructor.

I called ```super``` on the first line of the ```constructor()```, then set the ```usesLitter``` property on the second line. In a ```constructor()```, one must always call the super method before the ```this``` keyword can be used— if not, JavaScript will throw a reference error. To avoid reference errors, it is best practice to call ```super``` on the first line of subclass constructors.

Below, i create a new ```Cat``` instance and call its name with the same syntax as i did with the ```Dog``` class:

```
const bryceCat = new Cat('Bryce', false);
console.log(bryceCat._name); // output: Bryce
```

In the example above, i created a new instance the ```Cat``` class, named ```bryceCat```. I passed it ```'Bryce'``` and ```false``` for the ```name``` and ```usesLitter``` arguments. When i called ```console.log(bryceCat._name)``` the program prints, ```Bryce```.


When i called ```extends``` in a class declaration, all of the parent methods are available to the child class.

Below, i extend the ```Animal``` class to a ```Cat``` subclass.

```
class Animal {
  constructor(name) {
    this._name = name;
    this._behavior = 0;
  }

  get name() {
    return this._name;
  }

  get behavior() {
    return this._behavior;
  }

  incrementBehavior() {
    this._behavior++;
  }
}


class Cat extends Animal {
  constructor(name, usesLitter) {
    super(name);
    this._usesLitter = usesLitter;
  }
}

const bryceCat = new Cat('Bryce', false);
```

In the example above, the ```Cat``` class extends ```Animal```. As a result, the ```Cat``` class has access to the ```Animal``` getters and the ```.incrementBehavior()``` method.

Also in the code above, i create a ```Cat``` instance named ```bryceCat```. Because ```bryceCat``` has access to the ```name``` getter, the code below logs ```'Bryce'``` to the console.

```
console.log(bryceCat.name);
```

Since the ```extends``` keyword brings all of the parent’s getters and methods into the child class, ```bryceCat.name``` accesses the ```name``` getter and returns the value saved to the ```name``` property.

Considering a more involved example and try to answer the following question: What will the code below log to the console?

```
bryceCat.incrementBehavior(); // Call .incrementBehavior() on Cat instance
console.log(bryceCat.behavior); // Log value saved to behavior
```

The correct answer is ```1```. Because:

- The ```Cat``` class inherits the ```_behavior``` property, ```behavior``` getter, and the ```.incrementBehavior()``` method from the ```Animal``` class.

- When i created the ```bryceCat``` instance, the ```Animal``` constructor set the ```_behavior``` property to zero.

- The first line of code calls the inherited ```.incrementBehavior()``` method, which increases the ```bryceCat``` ```_behavior``` value from zero to one.

- The second line of code calls the ```behavior``` getter and logs the value saved to ```_behavior``` (```1```).

In addition to the inherited features, child classes can contain their own properties, getters, setters, and methods.

Below, i will add a ```usesLitter``` getter. The syntax for creating getters, setters, and methods is the same as it is in any other class.

```
class Cat extends Animal {
  constructor(name, usesLitter) {
    super(name);
    this._usesLitter = usesLitter;
  }

  get usesLitter() {
    return this._usesLitter;
  }
}
```

In the example above, i created a ```usesLitter``` getter in the ```Cat``` class that returns the value saved to ```_usesLitter```.

Comparing the ```Cat``` class above to the one i created without inheritance:

```
class Cat {
  constructor(name, usesLitter) {
    this._name = name;
    this._usesLitter = usesLitter;
    this._behavior = 0;
  }

  get name() {
    return this._name;
  }

  get usesLitter() {
    return this._usesLitter;
  }

  get behavior() {
    return this._behavior;
  }

  incrementBehavior() {
    this._behavior++;
  }
}
```

I decreased the number of lines required to create the ```Cat``` class by about half. Yes, it did require an extra class (```Animal```), making the reduction in the size of the ```Cat``` class seem moot. However, the benefits (time saved, readability, efficiency) of inheritance grow as the number and size of the subclasses increase.

One benefit is that when there is need to change a method or property that multiple classes share, i can change the parent class, instead of each subclass.

Before i move past inheritance, taking a moment to see how i would create an additional subclass, called ```Dog```.

```
class Dog extends Animal {
  constructor(name) {
    super(name);
  }
}
```

This ```Dog``` class has access to the same properties, getters, setters, and methods as the ```Dog``` class i made without inheritance, and is a quarter the size.

Now that i have abstracted animal daycare features, it’s easy to see how i can extend ```Animal``` to support other classes, like ```Rabbit```, ```Bird``` or even ```Snake```.


## Static Methods

Sometimes there will be need for a class to have methods that aren’t available in individual instances, but that can be called directly from the class.

Take the ```Date``` class, for example — i can both create ```Date``` instances to represent whatever date i want, and call static methods, like ```Date.now()``` which returns the current date, directly from the class. The ```.now()``` method is static, so i can call it directly from the class, but not from an instance of the class.

Using the ```static``` keyword to create a static method called ```generateName``` method in our ```Animal``` class:

```
class Animal {
  constructor(name) {
    this._name = name;
    this._behavior = 0;
  }

  static generateName() {
    const names = ['Angel', 'Spike', 'Buffy', 'Willow', 'Tara'];
    const randomNumber = Math.floor(Math.random()*5);
    return names[randomNumber];
  }
}
```

In the example above, i create a ```static``` method called ```.generateName()``` that returns a random name when it’s called. Because of the ```static``` keyword, i can only access ```.generateName()``` by appending it to the ```Animal``` class.

I call the ```.generateName()``` method with the following syntax:

```
console.log(Animal.generateName()); // returns a name
```

I cannot access the ```.generateName()``` method from instances of the ```Animal``` class or instances of its subclasses (See below).

```
const tyson = new Animal('Tyson');
tyson.generateName(); // TypeError
```

The example above will result in an error, because i cannot call static methods (```.generateName()```) on an instance (```tyson```).