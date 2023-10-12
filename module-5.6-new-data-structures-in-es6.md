**Module 5.6: New Data Structures in ES6**

ES6 (ECMAScript 2015) introduced several new data structures to JavaScript, enhancing the language's ability to manage and manipulate data efficiently. These new data structures provide alternatives to arrays and objects, offering specific benefits and improved performance in various use cases.

Let's explore some of these new data structures with examples:

### 1. Set

The `Set` data structure allows you to store unique values of any type, whether primitive or object references. It ensures that no duplicate values are stored.

```javascript
const uniqueNumbers = new Set();

uniqueNumbers.add(5);
uniqueNumbers.add(10);
uniqueNumbers.add(5); // Duplicate value, will be ignored

console.log(uniqueNumbers.size); // Outputs: 2

uniqueNumbers.forEach((value) => {
  console.log(value);
});
// Outputs:
// 5
// 10
```

In this example, the `Set` prevents the duplication of the number 5, resulting in a unique collection.

### 2. Map

The `Map` data structure allows you to store key-value pairs, providing efficient access to values based on their keys.

```javascript
const person = new Map();

person.set('name', 'Alice');
person.set('age', 30);

console.log(person.get('name')); // Outputs: 'Alice'
console.log(person.get('age')); // Outputs: 30

console.log(person.has('name')); // Outputs: true
console.log(person.has('email')); // Outputs: false

person.forEach((value, key) => {
  console.log(`${key}: ${value}`);
});
// Outputs:
// name: Alice
// age: 30
```

In this example, the `Map` data structure is used to store key-value pairs, providing efficient access to values by their keys.

### 3. WeakSet and WeakMap

`WeakSet` and `WeakMap` are similar to `Set` and `Map`, but they hold weak references to their elements. This means that objects in a `WeakSet` or `WeakMap` can be garbage-collected if no other references to them exist, which can be useful in scenarios like managing event handlers.

```javascript
const weakSet = new WeakSet();
const weakMap = new WeakMap();

const obj = {};

weakSet.add(obj);
weakMap.set(obj, 'some data');

console.log(weakSet.has(obj)); // Outputs: true
console.log(weakMap.get(obj)); // Outputs: 'some data'

// If you remove all references to 'obj', it may be garbage-collected
```

`WeakSet` and `WeakMap` allow you to associate metadata with objects while allowing them to be collected by the garbage collector when they are no longer needed.

### 4. Symbol

ES6 introduced the `Symbol` primitive data type, which can be used to create unique, non-enumerable property keys, especially in objects. This is useful for scenarios where you need to prevent naming collisions when adding properties to objects.

```javascript
const uniqueKey = Symbol('unique');
const obj = {
  name: 'Bob',
  age: 25,
  [uniqueKey]: 'some unique value',
};

console.log(obj[uniqueKey]); // Outputs: 'some unique value'
```

In this example, the `Symbol` is used as a unique key for the `obj` object, ensuring that it won't conflict with other property names.

### 5. Iterators and Generators

ES6 introduced a new iteration protocol that allows objects to define or customize their iteration behavior. This protocol is utilized by the `for...of` loop, enabling you to iterate over various data structures seamlessly.

```javascript
const iterableObject = {
  values: [1, 2, 3, 4],
  [Symbol.iterator]: function* () {
    for (let value of this.values) {
      yield value;
    }
  },
};

for (let item of iterableObject) {
  console.log(item);
}
// Outputs:
// 1
// 2
// 3
// 4
```

In this example, the `iterableObject` is defined as an iterable object, allowing you to use the `for...of` loop to iterate through its values.

### 6. Typed Arrays

Typed Arrays are a set of array-like objects for working with binary data. They provide memory-efficient ways to work with large binary data, such as audio buffers and image data.

```javascript
const buffer = new ArrayBuffer(16); // Create a 16-byte buffer
const int32View = new Int32Array(buffer); // Create a view to treat buffer as 4 32-bit integers

int32View[0] = 42;
int32View[1] = 100;

console.log(int32View[0]); // Outputs: 42
console.log(int32View[1]); // Outputs: 100
```

Typed Arrays are essential for applications that deal with low-level data, and they are more memory-efficient compared to traditional arrays.

### 7. Sets and Maps

ES6 introduced two new built-in data structures, Sets and Maps, which provide more efficient ways to manage collections of data.

#### Sets

A Set is a collection of values where each value must be unique. It can be used to remove duplicates from an array, check for the existence of elements, and more.

```javascript
const uniqueNumbers = new Set([1, 2, 3, 3, 4, 4, 5]);
console.log(uniqueNumbers); // Outputs: Set { 1, 2, 3, 4, 5 }

console.log(uniqueNumbers.has(3)); // Outputs: true
console.log(uniqueNumbers.size); // Outputs: 5

uniqueNumbers.add(6);
uniqueNumbers.delete(4);

console.log(uniqueNumbers); // Outputs: Set { 1, 2, 3, 5, 6 }
```

#### Maps

Maps are collections of key-value pairs. They are similar to objects but allow any value (including objects and primitive values) as keys.

```javascript
const person = new Map();
person.set('name', 'Alice');
person.set('age', 30);

console.log(person.get('name')); // Outputs: Alice
console.log(person.has('age')); // Outputs: true
console.log(person.size); // Outputs: 2

person.delete('age');

console.log(person); // Outputs: Map { 'name' => 'Alice' }
```

Maps are particularly useful when you need to associate data with specific keys and keep the insertion order.

### 8. Promises

Promises provide a more structured way to work with asynchronous operations, making it easier to handle success and error scenarios. They are a significant improvement over traditional callback patterns.

```javascript
function fetchData() {
  return new Promise((resolve, reject) => {
    // Simulate an asynchronous operation
    setTimeout(() => {
      const data = 'Some data';
      if (data) {
        resolve(data);
      } else {
        reject('Error occurred');
      }
    }, 1000);
  });
}

fetchData()
  .then((data) => {
    console.log('Success:', data);
  })
  .catch((error) => {
    console.error('Error:', error);
  });
```

Promises simplify error handling and make asynchronous code more readable and maintainable.

### 9. Proxy

The Proxy object is used to define custom behavior for fundamental operations like property lookup, assignment, enumeration, function invocation, and more. It's a powerful tool for creating custom traps and modifying objects' behavior.

```javascript
const target = {
  value: 42,
};

const handler = {
  get: function (obj, prop) {
    console.log(`Getting property "${prop}"`);
    return obj[prop];
  },
};

const proxy = new Proxy(target, handler);

console.log(proxy.value); // Outputs: Getting property "value", 42
```

Proxies open up possibilities for building advanced abstractions and security layers in your applications.

### 10. Reflect

The Reflect object provides a standard way for interacting with objects, similar to the `Proxy` object. It offers static methods for performing common object operations, and it complements the `Proxy` object well.

```javascript
const obj = {
  name: 'John',
  age: 30,
};

console.log(Reflect.has(obj, 'name')); // Outputs: true
console.log(Reflect.ownKeys(obj)); // Outputs: [ 'name', 'age' ]
```

`Reflect` is often used in conjunction with `Proxy` to implement custom behavior for object operations.

### 11. Template Literals

Template literals are an ES6 feature that allows you to embed expressions inside string literals, making it easier to create complex strings.

```javascript
const name = 'Alice';
const age = 30;

const message = `Hello, my name is ${name} and I am ${age} years old.`;
console.log(message); // Outputs: Hello, my name is Alice and I am 30 years old.
```

Template literals are more readable and concise than traditional string concatenation.

### 12. Modules

ES6 introduced a standardized module system for JavaScript, allowing developers to create reusable and organized code. Modules can export and import functions, objects, or values.

**Module Export:**

```javascript
// math.js
export function add(a, b) {
  return a + b;
}
```

**Module Import:**

```javascript
import { add } from './math.js';

console.log(add(2, 3)); // Outputs: 5
```

Modules help in maintaining clean and organized code, making it easier to collaborate and share code among projects.

### 13. Arrow Functions

Arrow functions provide a more concise syntax for writing function expressions. They are especially useful when working with callbacks and short functions.

```javascript
const numbers = [1, 2, 3, 4, 5];

// Traditional function
const doubled = numbers.map(function (number) {
  return number * 2;
});

// Arrow function
const doubled = numbers.map((number) => number * 2);
```

Arrow functions also capture the `this` value from their surrounding context, which can be useful in some situations.

### 14. Spread and Rest Operators

The spread (`...`) and rest (`...`) operators are powerful tools for working with arrays and objects.

**Spread Operator (Array):**

```javascript
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

const combined = [...arr1, ...arr2];
console.log(combined); // Outputs: [1, 2, 3, 4, 5, 6]
```

**Rest Operator (Function Parameters):**

```javascript
function sum(...numbers) {
  return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3)); // Outputs: 6
```

The spread and rest operators make working with data structures more flexible and concise.

### 15. Default Parameters

ES6 introduced default parameter values for functions, allowing you to provide default values when arguments are not passed.

```javascript
function greet(name = 'Guest') {
  console.log(`Hello, ${name}!`);
}

greet(); // Outputs: Hello, Guest!
greet('Alice'); // Outputs: Hello, Alice!
```

Default parameters make functions more robust and reduce the need for excessive argument checking.

### 16. Async/Await

Async/Await is a syntax for handling asynchronous operations, built on top of Promises. It simplifies asynchronous code, making it look more like synchronous code.

```javascript
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('Error:', error);
  }
}

fetchData()
  .then((data) => {
    console.log('Data:', data);
  });
```

Async/Await improves the readability of asynchronous code and error handling.

### 17. Map and Set

ES6 introduced two new built-in data structures: `Map` and `Set`.

**Map:**

```javascript
const userMap = new Map();
userMap.set('name', 'Alice');
userMap.set('age', 30);

console.log(userMap.get('name')); // Outputs: Alice
```

`Map` allows you to store key-value pairs and is especially useful when you need to associate data with unique keys.

**Set:**

```javascript
const uniqueNumbers = new Set();
uniqueNumbers.add(1);
uniqueNumbers.add(2);
uniqueNumbers.add(1);

console.log(uniqueNumbers.size); // Outputs: 2
```

`Set` stores unique values, ensuring that no duplicates are allowed.

### 18. Classes

ES6 introduced class syntax for defining object constructors, making it more similar to class-based languages.

```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
  }
}

const alice = new Person('Alice', 30);
alice.greet(); // Outputs: Hello, my name is Alice and I am 30 years old.
```

Classes offer a more structured way to create and manage objects and their methods.

### 19. Promises

Promises were introduced to simplify and improve asynchronous code handling.

```javascript
function fetchData() {
  return new Promise((resolve, reject) => {
    fetch('https://api.example.com/data')
      .then((response) => response.json())
      .then((data) => resolve(data))
      .catch((error) => reject(error));
  });
}

fetchData()
  .then((data) => {
    console.log('Data:', data);
  })
  .catch((error) => {
    console.error('Error:', error);
  });
```

Promises offer a more organized way to handle asynchronous operations and handle success and error cases.

### 20. Fetch API

The Fetch API simplifies making network requests. It provides a more modern and flexible alternative to the older `XMLHttpRequest`.

```javascript
fetch('https://api.example.com/data')
  .then((response) => response.json())
  .then((data) => console.log('Data:', data))
  .catch((error) => console.error('Error:', error));
```

The Fetch API is more intuitive and returns Promises for handling responses.
