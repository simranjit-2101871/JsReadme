# Callback Function in JavaScript

A **callback function** is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action.

There are two ways in which the callback may be called: **synchronous** and **asynchronous**.  

- **Synchronous callbacks** are called immediately after the invocation of the outer function, with no intervening asynchronous tasks.
- **Asynchronous callbacks** are called later, after an asynchronous operation has completed.

---

## Limitations of Arrow Functions

Arrow functions in JavaScript have some important limitations:

1. **No `this` binding**  
   - Arrow functions do not have their own `this`. Instead, they inherit `this` from the surrounding scope.

2. **No `arguments` object**  
   - Arrow functions do not have their own `arguments` object.

3. **Cannot be used as methods**  
   - Arrow functions should not be used as methods in objects because they do not bind `this`.

4. **Cannot be used as constructors**  
   - Calling an arrow function with `new` throws a `TypeError`.

5. **Cannot use `yield`**  
   - Arrow functions cannot be used as generator functions.

---

## Converting Traditional Functions to Arrow Functions

Let's break down a traditional function into an arrow function step by step:

```js
// Traditional function
(function(a) {
    return a + 100;
});

// Step 1: Remove the 'function' keyword
(d) => {
    return d + 100;
};

// Step 2: Remove the function body braces if it contains a single expression
(b) => b + 100;

// Step 3: Remove the parentheses if there is a single argument
e => e + 100;

        e=>e+100;
```


>The braces can only be omitted if the function directly returns an expression. If the body has statements, the braces are required — and so   is the return keyword. Arrow functions cannot guess what or when you want to return.


**Function body** 
Arrow functions can have either an expression body or the usual block body.

In an expression body, only a single expression is specified, which becomes the implicit return value. In a block body, you must use an explicit return statement.

```
                // Traditional anonymous function
        (function (a, b) {
            const chuck = 42;
            return a + b + chuck;
        });

        (a, b) => {
            const tom = 23;
            return a + b + tom;
        };

        //function as aexpression
        const func = (x) => x * x;
        // expression body syntax, implied "return"

        const func2 = (x, y) => {
            return x + y;
        };
        // with block body, explicit "return" needed
```