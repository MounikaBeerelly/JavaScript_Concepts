# Functions vs Arrow Functions

1. **Syntax** -
- Function : Uses the function keyword.
    ```
    function greet(name) {
        return `Hello ${name}`!;
    }
    ```
- Arrow Function : Uses the => arrow syntax.
    ```
    const greet = (name) => `Hello ${name}`!;
    ```
2. **Hoisting** -
- Function: Functions are hoisted, meaning they can be called before they are defined.
    ```
    console.log(greet('Mounika')); // Hello, Mounika!
    function greet(name) {
        return `Hello, ${name}`!;
    }
    ```
- Arrow Function: Not hoisted, must be defined before being called.
    ```
    console.log(greet('Mounika')); //Error: greet is not defined
    const greet = (name) => `Hello, ${name}`!;
    ```
3. **this binding** -
- Function: Has its own this, determined by how the function is called.
    ```
    function Person() {
        this.name = "Avyay";
        setTimeout(function () {
            console.log(this.name); // Undefined (depends on how it's called)
        }, 1000);
    }
    new Person();
    ```
- Arrow Function: Inherits this from the surrounding context (lexical this).
    ```
    function Person() {
        this.name = "Avyay";
        setTimeout(() => {
            console.log(this.name); // Avyay (inherits from the enclosing scope)
        }, 1000);
    }
    new Person();
    ```
4. **Arguments Object** -
- Function : Has access to the arguments object, an array-like object holding all passed arguments.
    ```
    function showArgs() {
        console.log(arguments); // log all arguments
    }
    showArgs(1,2,3); // [1,2,3]
    ```
- Arrow Function : Does not have its own arguments object. Use rest parameters instead.
    ```
    const showArgs = (...arguments) => {
        console.log(arguments); // Use rest parameters
    }
    showArgs(1,2,3); // [1,2,3]
    ```
5. **Return Statement** -
- Function : Requires return for returning values (unless using shorthand).
    ```
    function add(a,b) {
        return a+b; // explicit return
    }
    console.log(add(3,6)); // 8
    ```
- Arrow Function : Allows implicit return for single-line expressions.
    ```
    const add = (a,b) => a+b; //implicit return
    console.log(add(3,6)); // 8
    ```
6. **Use Case** - 
- Function : Use for defining methods, event handlers, complex functions.
    ```
    // Function for defing methods
    const Person = {
        name: "Avi",
        greet : function () {
            console.log(`Hello, ${this.name}!`); 
        },
    };
    ```
- Arrow Function: Use for callbacks, array methods (map, reduce, filter), or inline logic.
    ```
    // Arrow function for callbacks
    const numbers = [1,2,3,4];
    const squares = numbers.map((n) => n*n);
    console.log(squares); // [1,4,9,16]
    ```