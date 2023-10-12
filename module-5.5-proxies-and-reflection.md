## Module 5.5: Proxies and Reflection

Proxies and Reflection are advanced JavaScript features that enable you to intercept and manipulate object behavior. Proxies allow you to create custom behavior for fundamental operations on objects, like property access, assignment, and method invocation. Reflection, on the other hand, provides a set of built-in JavaScript methods for introspection.

### 1. Proxies

Proxies are objects used for defining custom behavior for fundamental operations (e.g., property lookup, assignment, enumeration, function invocation, etc.) on JavaScript objects. Proxies are created using the `Proxy` constructor. Here's an example of using proxies to intercept and modify property access:

```javascript
const target = { name: 'Alice' };

const handler = {
  get: function (obj, prop) {
    if (prop in obj) {
      return obj[prop];
    }
    return `Property '${prop}' doesn't exist.`;
  },
};

const proxy = new Proxy(target, handler);

console.log(proxy.name); // Outputs: "Alice"
console.log(proxy.age); // Outputs: "Property 'age' doesn't exist."
```

In this example, the `handler` defines a custom behavior for property access. If the property exists in the `target` object, it returns the property value. Otherwise, it returns a custom message.

### 2. Proxy Traps

Proxy objects can define various traps that allow you to intercept and customize different operations, including:

- `get`: Called when a property is read.
- `set`: Called when a property is assigned.
- `apply`: Called when a function is invoked.
- Many more...

Here's an example demonstrating the `set` trap:

```javascript
const target = { x: 10, y: 20 };

const handler = {
  set: function (obj, prop, value) {
    if (prop === 'sum') {
      obj.x = value;
      obj.y = value;
    } else {
      obj[prop] = value;
    }
    return true; // Indicates success
  },
};

const proxy = new Proxy(target, handler);

proxy.x = 30;
console.log(proxy.x); // Outputs: 30
proxy.sum = 50; // Sets both x and y to 50
console.log(proxy.x); // Outputs: 50
console.log(proxy.y); // Outputs: 50
```

In this example, the `set` trap allows us to customize how properties are set. When the 'sum' property is set, it modifies both 'x' and 'y' to the same value.

### 3. Reflection

JavaScript provides built-in reflection features that allow you to inspect and manipulate objects. These methods are available under the `Reflect` object. Here's an example:

```javascript
const obj = { name: 'Bob', age: 30 };

console.log(Reflect.has(obj, 'name')); // Outputs: true
console.log(Reflect.ownKeys(obj)); // Outputs: ['name', 'age']
```

In this example, `Reflect.has` checks if the 'name' property exists in the object, and `Reflect.ownKeys` returns an array of an object's own property keys.

Proxies and Reflection provide powerful tools for creating custom object behavior and introspecting objects, enhancing the capabilities of JavaScript, especially when building advanced applications and frameworks.
