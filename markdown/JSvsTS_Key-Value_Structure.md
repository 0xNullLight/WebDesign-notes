
### Key-Value Structures in TypeScript vs JavaScript with Nested Functions

#### Overview
Key-value structures like **objects** and **Maps** exist in both JavaScript and TypeScript.

***JavaScript*** offers flexibility through ***dynamic typing***.
***TypeScript*** enforces ***static typing*** to catch potential errors early.

Nested functions, which are functions defined within other functions, can be used to organize code better.

### 1. **Objects**
Objects store key-value pairs, and methods (functions) can be values within an object.

- **JavaScript**: 
  Dynamic typing allows you to add any type of function within an object, and you can also nest functions inside these methods.

  ```javascript
  const employee = {
    name: "John",  // string key-value pair
    age: 30,       // number key-value pair
    greet() {      // method (function as a value)
      // Nested function inside the greet method
      const sayHello = () => {
        console.log(`Hello, my name is ${this.name}`); // Accessing object property using `this`
      };
      
      // Call the nested function
      sayHello(); 
    },
  };

  // Call the greet method
  employee.greet(); // Output: Hello, my name is John
  ```

- **TypeScript**: 
  TypeScript allows you to define the types for both the object properties and the methods. You can also define types for the nested functions within the methods.

  ```typescript
  const employee: { 
    name: string;  // name must be a string
    age: number;   // age must be a number
    greet: () => void; // greet method must be a function that returns void
  } = {
    name: "John",
    age: 30,
    greet() {
      // Nested function inside greet method
      const sayHello = (): void => { 
        console.log(`Hello, my name is ${this.name}`);
      };

      // Call the nested function
      sayHello(); 
    },
  };

  // Call the greet method
  employee.greet(); // Output: Hello, my name is John
  ```

### 2. **Maps**
With `Map`, you can store functions as values and nest other functions inside them.

- **JavaScript**: 
  Dynamic typing allows storing different types of values in a `Map`, including functions that may contain nested logic.

  ```javascript
  const map = new Map();

  // Set a function as a value for the key "greet"
  map.set("greet", () => {
    // Nested function within the mapped function
    const sayHello = () => {
      console.log("Hello!");
    };
    
    // Call the nested function
    sayHello();
  });

  // Retrieve and call the function stored under the "greet" key
  map.get("greet")(); // Output: Hello!
  ```

- **TypeScript**: 
  TypeScript ensures that both keys and values in the `Map` follow specific types. You can define the type of keys and the return type of the functions stored in the `Map`.

  ```typescript
  // Define a Map with string keys and void-returning functions as values
  const map: Map<string, () => void> = new Map();

  // Set a function as a value for the key "greet"
  map.set("greet", (): void => {
    // Nested function within the main function
    const sayHello = (): void => {
      console.log("Hello from nested function!");
    };

    // Call the nested function
    sayHello();
  });

  // Retrieve and call the function stored under the "greet" key
  map.get("greet")(); // Output: Hello from nested function!
  ```

### 3. **Utility Types: `Record` with Nested Functions**
The `Record` utility type in TypeScript lets you create key-value objects with specific types for both the keys and values. Functions can be used as values, and nested functions can be defined within these functions.

- **TypeScript**:
  ```typescript
  // Define a Record type where all keys are strings and all values are functions that return void
  type EmployeeRecord = Record<string, () => void>;

  // Create an object that adheres to the EmployeeRecord type
  const employeeActions: EmployeeRecord = {
    // Method that logs a message, containing a nested function
    greet() {
      // Nested function within the greet method
      const nestedGreet = (): void => {
        console.log("Nested: Hello, employee!");
      };

      // Call the nested function
      nestedGreet();
    },
  };

  // Call the greet method
  employeeActions.greet(); // Output: Nested: Hello, employee!
  ```

### Nesting Functions for Reusability
Nested functions are useful for encapsulating related logic inside a larger function. This promotes code modularity, making it more readable and easier to maintain.

### Summary
- **JavaScript**: Offers flexibility in key-value structures and nested functions but lacks type safety.
- **TypeScript**: Adds the power of static typing, ensuring consistency in key-value structures and functions. This helps catch type errors early, even when using nested functions inside methods.
