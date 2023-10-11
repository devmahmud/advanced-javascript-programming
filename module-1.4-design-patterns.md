## Module 1: Advanced JavaScript Concepts
### 1.4. Design Patterns

Design patterns are reusable solutions to common problems that arise during software design and development. In JavaScript, as in any other programming language, design patterns help developers create maintainable and efficient code by following established best practices. Let's explore some design patterns in-depth with examples:

### 1. Singleton Pattern:

The Singleton pattern ensures that a class has only one instance and provides a global point of access to that instance. It's useful when exactly one object is needed to coordinate actions across a system.

**Example: Singleton Pattern**

```javascript
const Singleton = (function () {
  let instance;
  
  function createInstance() {
    return {
      data: "This is the singleton instance."
    };
  }
  
  return {
    getInstance: function () {
      if (!instance) {
        instance = createInstance();
      }
      return instance;
    }
  };
})();

const instance1 = Singleton.getInstance();
const instance2 = Singleton.getInstance();

console.log(instance1 === instance2); // true
console.log(instance1.data); // "This is the singleton instance."
```

In this example, the Singleton pattern ensures that there's only one instance of the `Singleton` object.

### 2. Factory Pattern:

The Factory pattern is used for creating objects without specifying the exact class of the object that will be created. It defines an interface for creating objects, but the specific object is determined at runtime.

**Example: Factory Pattern**

```javascript
class Circle {
  constructor(radius) {
    this.radius = radius;
  }
}

class Square {
  constructor(sideLength) {
    this.sideLength = sideLength;
  }
}

function createShape(type, size) {
  if (type === "circle") {
    return new Circle(size);
  } else if (type === "square") {
    return new Square(size);
  }
}

const circle = createShape("circle", 5);
const square = createShape("square", 4);

console.log(circle instanceof Circle); // true
console.log(square instanceof Square); // true
```

The Factory pattern allows us to create objects (shapes in this case) without needing to know the specific class details.

### 3. Observer Pattern:

The Observer pattern is used when an object (the subject) maintains a list of its dependents (observers) and notifies them of state changes, typically by calling one of their methods.

**Example: Observer Pattern**

```javascript
class Subject {
  constructor() {
    this.observers = [];
  }
  
  addObserver(observer) {
    this.observers.push(observer);
  }
  
  removeObserver(observer) {
    this.observers = this.observers.filter(obs => obs !== observer);
  }
  
  notify(message) {
    this.observers.forEach(observer => observer.update(message));
  }
}

class Observer {
  update(message) {
    console.log("Received message:", message);
  }
}

const subject = new Subject();
const observer1 = new Observer();
const observer2 = new Observer();

subject.addObserver(observer1);
subject.addObserver(observer2);

subject.notify("Hello, observers!");
```

In this example, the `Observer` pattern allows multiple observers to be notified when the subject's state changes.

### 4. Module Pattern:

The Module pattern allows you to create private and public encapsulation for your code, making it more organized and less prone to conflicts.

**Example: Module Pattern**

```javascript
const Module = (function () {
  // Private variable
  let privateVar = 10;
  
  // Private function
  function privateFunction() {
    return privateVar;
  }
  
  // Public interface
  return {
    publicFunction: function () {
      return privateFunction();
    },
    changeVar: function (newValue) {
      privateVar = newValue;
    }
  };
})();

console.log(Module.publicFunction()); // 10
Module.changeVar(20);
console.log(Module.publicFunction()); // 20
```

The Module pattern allows for the creation of public and private members, promoting encapsulation.

These are just a few examples of design patterns in JavaScript. Design patterns provide a structured approach to solving common software design problems, making your code more organized, efficient, and maintainable. Depending on the situation, different patterns can be applied to solve specific issues in your code.