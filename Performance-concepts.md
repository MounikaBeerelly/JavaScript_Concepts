## JavaScript Performance Tips

1. **Use Strict Mode :**
- Enabling strict mode in JavaScript catches common coding bloopers, prevents the use of undeclared variables, and makes your code run faster.
- “use strict;” can tell the browser to execute in strict mode, which can improve the performance.
    ```
    "use strict";
    function myFunc() {
        // 
    }
    ```
2. **Minimize DOM Manipulation :**
- Manipulating the Document Object Model (DOM) is one of the slowest operations in JavaScript. 
- Reducing the number of direct DOM manipulations can significantly improve performance.
**Instead of:**
    ```
    const list = document.getElementById('myList');
    const items = ['item1', 'item2','item3'];
    
    items.forEach((item) => {
        const li = document.createElement("li");
        li.textcontent = item;
        list.appendChild(li);
    });
    ```
**Use Document Fragments**
    ```
    const list = document.getElementById('myList');
    const items = ['item1', 'item2','item3'];
    const fragment = document.createDocumentFragment();
    ```
- By using a document fragment, you batch your DOM updates, which is much more efficient.
- Personal Note: After switching to document fragments in a dynamic list, I noticed a significant reduction in rendering time, especially with large datasets.
3. **Use Event Delegation**
- Attaching event listeners to multiple DOM elements can be inefficient. Event delegation allows you to handle events at a higher level in the DOM.
- Instead of:
    ```
    const buttons = document.querySelectorAll('.myButton');
    buttons.forEach(button => {
        button.addEventListener("click", function() {
            // handleClick()
        });
    });
    ```
- Use Event Delegation:
    ```
    document.body.addEventListener('click', function(event) {
        if(event.target.classList.contains('myButton')) {
            // handleClick ()
        }
    })
    ```
4. **Avoid Memory Leaks :**
- Attaching event listeners to multiple DOM elements can be inefficient. Event delegation allows you to handle events at a higher level in the DOM.
- Common Pitfall:
    ```
    let element = document.getElementById("myElement");
    element.addEventListener("click", function() {
            console.log('Clcikced');
    });
    // later in the code
    element = null;  // this doesn't remove the event listener
    ```
- Proper Cleanup :
     ```
    let element = document.getElementById("myElement");
    function handleClick() {
        console.log('Clcikced');
    }
    element.addEventListener("click", handleClick);
    // later in the code
    element.removeEventListener("click", handleClick);
    element = null;
    ```