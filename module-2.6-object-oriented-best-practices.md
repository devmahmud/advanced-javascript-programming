#### Module 2.6: Object-Oriented Best Practices

In this module, you will delve into object-oriented best practices in JavaScript. Object-oriented programming (OOP) plays a crucial role in structuring your code and promoting reusability. By following these best practices, you can create maintainable and efficient code. Let's explore these practices in-depth with examples.

##### Encapsulation

Encapsulation is a fundamental OOP concept that involves bundling data (attributes) and methods (functions) that operate on that data into a single unit, known as a class. In JavaScript, you can achieve encapsulation using constructor functions, classes, or closures.

**Example: Using Classes**

```javascript
class Car {
  constructor(make, model) {
    this.make = make;
    this.model = model;
  }

  drive() {
    console.log(`Driving the ${this.make} ${this.model}`);
  }
}

const myCar = new Car('Toyota', 'Camry');
myCar.drive(); // Output: Driving the Toyota Camry
```

### Inheritance

Inheritance allows you to create a new class based on an existing class, inheriting its properties and methods. This promotes code reuse and maintains a hierarchical structure.

**Example: Using Classes**

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a sound`);
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name);
    this.breed = breed;
  }

  speak() {
    console.log(`${this.name} barks`);
  }
}

const myDog = new Dog('Buddy', 'Golden Retriever');
myDog.speak(); // Output: Buddy barks
```

### Polymorphism

Polymorphism enables different objects to be treated as instances of a common base class, allowing them to be used interchangeably.

**Example: Using Classes**

```javascript
class Shape {
  area() {
    return 0;
  }
}

class Circle extends Shape {
  constructor(radius) {
    super();
    this.radius = radius;
  }

  area() {
    return Math.PI * this.radius ** 2;
  }
}

class Rectangle extends Shape {
  constructor(width, height) {
    super();
    this.width = width;
    this.height = height;
  }

  area() {
    return this.width * this.height;
  }
}

function calculateArea(shape) {
  return shape.area();
}

const myCircle = new Circle(5);
const myRectangle = new Rectangle(4, 6);

console.log(calculateArea(myCircle)); // Output: 78.54
console.log(calculateArea(myRectangle)); // Output: 24
```

### These are some of the best practices for object-oriented programming in JavaScript. By following these practices, you can write clean and maintainable code that is easier to extend and modify.
