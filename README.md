# JavaScript_Concepts

- Main concepts in JavaScript : 

1. Arrow Functions
    - Arrow functions provide a concise way to write javascript function expressions.
    
    ```
    const greet = name => `Hello, ${name}!`;
    console.log(greet('Mounika')); // Hello Mounika!
    ```

2. Map and Filter
    - ***Map*** : Creates new array by trnasfforming each element.
    - ***Filter*** : Creates new array with elements that passes a test.

    ```
    const numbers = [1, 2, 3, 4, 5];
    const doubled = numbers.map(num => num * 2);
    const evenNumbers = numbers.filter(num => num%2 === 0); 
    console.log('Doubled', doubled); [2, 4, 6, 8, 10]
    console.log('Evens', evenNumbers); // [2,4]
    ```
3. Slice() and Splice()
    - ***Slice*** : Returns a shallow copy of an array.
    - ***Splice*** : Changes the contents of an array by removing or replacing existing elements and/or adding new elements.
    
    ```
    const fruits = ['apple', 'banana', 'cherry', 'grapes'];
    console.log('Slice', fruits.slice(1,3)); // ['banana', 'cherry']
    console.log('Original after slice:', fruits); // ['apple', 'banana', 'cherry', 'grapes']

    const veggies = ['tomato', 'potato', 'carrot', 'broccoli'];
    console.log('Splice', veggies.splice(1,2, 'beans')); // ['potato', 'carrot']
    console.log('Original after splice:', veggies); // ['tomato', 'beans', 'broccoli']
    ```
4. Destructuring
    - Allows you to extract vlaues from objects or arrays into distinct variables.

    ```
    const person = { name: 'John', age: 30, job: 'Developer'};
    const { name, age } = person;
    console.log(`${name} is ${age} years old.`);  // John is 30 years old.

    const colors = ['red', 'green', 'blue', 'white'];
    const [firstColor, secondcolor] = colors;
    console.log(`First Color: ${firstColor}, Second Color: ${secondColor}`); // First Color: red, Second Color: green
    ```
5. Rest and Spread Operators
    - Rest operator collects multiple elements into an array.
    - Spread operator expands an iterable into individual elements.

    ```
    const sum = (...numbers) => numbers.reduce((acc,num) => acc + num, 0);
    console.log('Sum:', sum(1,2,3,4,5)); // 15

    const arr1 = [1, 2, 3];
    const arr2 = [4, 5, 6];
    const combined = [...arr1, ...arr2];
    console.log('Combined array:', combined); //[1, 2, 3, 4, 5, 6]
    ```
6. Template Literals
    - Template literals allow embedded expressions and multi-line strings.

    ```
    const name = 'React';
    const version = 18;
    const greeting = `Heelo, ${name}!
        You are using version ${version}.
        Welcome to the world of web development. `;
    console.log(greeting); // Hello React!, You are using version 18. Welcome to the world of web development.
    ```
7. Promises and Async/Await
    - Used for handling asynchronous operations.

    ```
    const fetchData = () => {
        return new Promise(resolve => {
            setTimeout(() => resolve('Data fetched'), 2000);
        });
    };

    async function getData() {
        console.log('Fetching data...');
        const result = await fetchData();
        console.log(result);
    };
    getData();
    ```