#### 2.2. Classes and Inheritance

With the introduction of ES6, JavaScript also supports class syntax for creating objects and implementing inheritance. Classes provide a more structured and familiar way of implementing object-oriented principles.

##### Classes in JavaScript

Here's an example of defining a class in JavaScript:

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a sound.`);
  }
}

const dog = new Animal('Buddy');
dog.speak(); // Output: Buddy makes a sound.
```

Classes encapsulate data and behavior, providing a clear and organized structure for your objects. In the example, we define an `Animal` class with a constructor method for initialization and a `speak` method for behavior. Instances of the class, like `dog`, can access these methods and properties.

##### Inheritance in ES6

Inheritance allows a class to inherit properties and methods from another class. For example, you can create a subclass `Dog` that inherits from `Animal`:

```javascript
class Dog extends Animal {
  constructor(name, breed) {
    super(name); // Calls the parent class constructor
    this.breed = breed;
  }

  speak() {
    console.log(`${this.name} barks.`);
  }
}

const goldenRetriever = new Dog('Max', 'Golden Retriever');
goldenRetriever.speak(); // Output: Max barks.
```

In this example, the `Dog` class inherits the `speak` method from the `Animal` class but overrides it to provide a more specific behavior (barking). The `super` keyword is used to call the parent class constructor and initialize the inherited properties.

#### Key Concepts

- **Classes:** Classes provide a structured way to create objects in JavaScript. They consist of a constructor method for object initialization and other methods for object behavior.

- **Inheritance:** Inheritance allows a subclass to inherit properties and methods from a parent class. ES6 introduced the `extends` keyword for easy implementation of inheritance.

- **super:** The `super` keyword is used in the constructor of a subclass to call the constructor of the parent class, ensuring proper initialization of inherited properties.

- **Method Overriding:** Subclasses can override inherited methods to provide specific behavior while still having access to the parent class's methods.

#### Benefits of Classes and Inheritance

- Classes provide a more structured and familiar way to create objects, making your code easier to understand and maintain.

- Inheritance promotes code reuse by allowing you to create hierarchies of objects with shared properties and behaviors.

- Method overriding in subclasses enables you to create specialized behavior for specific types of objects while maintaining a consistent interface.

Understanding Classes and Inheritance is essential for mastering Object-Oriented Programming in JavaScript, as they enable you to create organized, efficient, and maintainable code.
