#### 2.5. Design Patterns in JavaScript

Design patterns are reusable solutions to common problems in software development. They provide a structured way to solve recurring design issues and improve code maintainability. In JavaScript, you can apply various design patterns to enhance the structure of your applications. Let's explore some key design patterns and provide examples of their use:

##### Singleton Pattern

The Singleton pattern ensures that a class has only one instance and provides a global point of access to that instance. It's useful when you need a single point of control for actions like logging, database connections, or application configuration.

**Example:**

```javascript
class SingletonDatabase {
  constructor(data) {
    if (SingletonDatabase.exists) {
      return SingletonDatabase.instance;
    }

    this.data = data;
    SingletonDatabase.instance = this;
    SingletonDatabase.exists = true;
    return this;
  }

  getData() {
    return this.data;
  }
}

const database1 = new SingletonDatabase('First database');
const database2 = new SingletonDatabase('Second database');

console.log(database1.getData()); // Output: "First database"
console.log(database1 === database2); // Output: true
```

### Factory Pattern

The Factory pattern is used to create objects without exposing the instantiation logic. It defines an interface for creating an object, but lets subclasses alter the type of objects that will be created.

**Example:**

```javascript
class Product {
  constructor(name, price) {
    this.name = name;
    this.price = price;
  }
}

class ProductFactory {
  createProduct(name, price) {
    return new Product(name, price);
  }
}

const factory = new ProductFactory();
const product1 = factory.createProduct('Widget', 10.0);
const product2 = factory.createProduct('Gadget', 15.0);

console.log(product1); // Output: Product { name: "Widget", price: 10 }
console.log(product2); // Output: Product { name: "Gadget", price: 15 }
```

### Observer Pattern

The Observer pattern defines a one-to-many dependency between objects so that when one object changes its state, all its dependents are notified and updated automatically.

**Example:**

```javascript
class Subject {
  constructor() {
    this.observers = [];
  }

  addObserver(observer) {
    this.observers.push(observer);
  }

  removeObserver(observer) {
    this.observers = this.observers.filter((obs) => obs !== observer);
  }

  notify(data) {
    this.observers.forEach((observer) => observer.update(data));
  }
}

class Observer {
  update(data) {
    console.log(`Received data: ${data}`);
  }
}

const subject = new Subject();
const observer1 = new Observer();
const observer2 = new Observer();

subject.addObserver(observer1);
subject.addObserver(observer2);

subject.notify('Some data has changed');
// Output:
// Received data: Some data has changed
// Received data: Some data has changed
```

These examples illustrate just a few design patterns in JavaScript. Design patterns help maintain clean, scalable, and more easily understandable code by providing tested and proven development paradigms. Understanding and applying these patterns can greatly benefit your JavaScript development skills.
