#### Module 2.8: Real-world OOP Examples

In this module, you will dive into real-world examples of applying Object-Oriented Programming (OOP) principles in JavaScript. These examples will showcase how OOP can be used to create well-structured and maintainable code for common scenarios. Let's explore these real-world examples:

##### Example 1: Building a ToDo List Application

Suppose you want to create a ToDo list application using OOP. Here's an example of how you might structure your code:

```javascript
class Task {
  constructor(id, description, completed) {
    this.id = id;
    this.description = description;
    this.completed = completed;
  }
}

class ToDoList {
  constructor() {
    this.tasks = [];
  }

  addTask(description) {
    const id = this.tasks.length + 1;
    const task = new Task(id, description, false);
    this.tasks.push(task);
  }

  markTaskAsCompleted(id) {
    const task = this.tasks.find((t) => t.id === id);
    if (task) {
      task.completed = true;
    }
  }

  getTasks() {
    return this.tasks;
  }
}
```

This code demonstrates the use of classes to model tasks and ToDo lists, encapsulating their properties and behavior.

### Example 2: Building a Car Rental System

Imagine you're creating a car rental system. OOP can help you structure your code effectively:

```javascript
class Car {
  constructor(id, brand, model, year, available) {
    this.id = id;
    this.brand = brand;
    this.model = model;
    this.year = year;
    this.available = available;
  }
}

class CarRentalSystem {
  constructor() {
    this.cars = [];
  }

  addCar(brand, model, year) {
    const id = this.cars.length + 1;
    const car = new Car(id, brand, model, year, true);
    this.cars.push(car);
  }

  rentCar(id) {
    const car = this.cars.find((c) => c.id === id);
    if (car && car.available) {
      car.available = false;
      return 'Car rented successfully';
    }
    return 'Car not available for rent';
  }

  getCars() {
    return this.cars;
  }
}
```

This example shows how OOP principles can help manage cars and rentals in a structured way.

### Example 3: Implementing a User Authentication System

OOP can also be applied to create user authentication systems:

```javascript
class User {
  constructor(username, password) {
    this.username = username;
    this.password = password;
  }

  authenticate(inputPassword) {
    return this.password === inputPassword;
  }
}

class AuthenticationSystem {
  constructor() {
    this.users = [];
  }

  registerUser(username, password) {
    const user = new User(username, password);
    this.users.push(user);
  }

  authenticateUser(username, password) {
    const user = this.users.find((u) => u.username === username);
    if (user) {
      return user.authenticate(password);
    }
    return false;
  }
}
```

In this example, OOP principles are applied to model users and an authentication system, encapsulating authentication logic.

These real-world examples demonstrate how Object-Oriented Programming can be applied to create well-structured and maintainable code for a variety of applications. By using classes and objects, you can encapsulate data and behavior, making your code more organized and easier to maintain.
