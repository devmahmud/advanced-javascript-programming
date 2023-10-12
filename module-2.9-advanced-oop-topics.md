#### Module 2.9: Advanced OOP Topics

In this module, we will delve into advanced Object-Oriented Programming (OOP) topics in JavaScript. These topics are essential for creating scalable and maintainable applications. Let's explore these advanced OOP concepts with examples:

##### 1. Composition over Inheritance

Composition is a powerful OOP concept that involves building complex objects by combining simpler ones. It's often preferred over class inheritance for creating flexible and maintainable code. Here's an example:

```javascript
class Engine {
  start() {
    console.log('Engine started');
  }
}

class Wheels {
  rotate() {
    console.log('Wheels rotating');
  }
}

class Car {
  constructor() {
    this.engine = new Engine();
    this.wheels = new Wheels();
  }

  drive() {
    this.engine.start();
    this.wheels.rotate();
    console.log('Car is moving');
  }
}

const myCar = new Car();
myCar.drive();
```

In this example, we use composition to create a `Car` object that contains an `Engine` and `Wheels`. This approach allows us to assemble complex objects from simpler parts.

### 2. Polymorphism

Polymorphism is a fundamental OOP concept that allows objects of different classes to be treated as objects of a common super-class. This promotes code reusability and flexibility. Here's an example using JavaScript's duck typing:

```javascript
class Bird {
  makeSound() {
    console.log('Bird is making a sound');
  }
}

class Dog {
  makeSound() {
    console.log('Dog is making a sound');
  }
}

function animalMakesSound(animal) {
  animal.makeSound();
}

const bird = new Bird();
const dog = new Dog();

animalMakesSound(bird); // Bird is making a sound
animalMakesSound(dog);  // Dog is making a sound
```

In this example, both `Bird` and `Dog` classes have a `makeSound` method. The `animalMakesSound` function can accept any object with this method, demonstrating polymorphism.

### 3. Encapsulation and Access Modifiers

Encapsulation involves bundling data (attributes) and methods (functions) into a single unit, i.e., a class. Access modifiers like public, private, and protected control the visibility and accessibility of class members. While JavaScript doesn't have native access modifiers, libraries like TypeScript provide support:

```javascript
class BankAccount {
  private balance: number = 0;

  deposit(amount: number) {
    this.balance += amount;
  }

  withdraw(amount: number) {
    if (amount <= this.balance) {
      this.balance -= amount;
    }
  }

  getBalance() {
    return this.balance;
  }
}

const account = new BankAccount();
account.deposit(1000);
account.withdraw(500);
console.log(account.getBalance()); // 500
```

In this TypeScript example, the `balance` property is private, ensuring it's only accessible within the `BankAccount` class.

These advanced OOP concepts, including composition, polymorphism, and encapsulation, are crucial for building complex, maintainable applications in JavaScript. By mastering these concepts, you can create scalable and flexible code.
