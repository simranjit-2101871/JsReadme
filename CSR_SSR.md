## Server side rendering vs Client side rendering

**SSR (Server-Side Rendering)**
The server does the rendering.
1.) browser just displays what it receives.
2.) No need for JavaScript in the browser to fetch data or render content.


**CSR (Client-Side Rendering)**
1.) The server only sends a basic empty HTML file.
2.) The browser uses JavaScript to dynamically fill in the content.


>Note->JavaScript is required to execute and display the page correctly.
    Why Doesn't SSR Need a JS Logic File?
    In SSR, the server itself creates the final HTML.
    When the browser receives the page, it's already filled with content.
    The browser just shows it—there's no need for extra JavaScript logic to process the content.
    🔹 In CSR, JavaScript is required to generate content.
    🔹 In SSR, the HTML is already complete, so no JavaScript is required on the client side.


Simple Analogy
Imagine you order a pizza.

CSR: The server sends you just the pizza dough, and you (the browser) must cook the toppings yourself.
SSR: The server sends you a fully cooked pizza, ready to eat.
🔹 In CSR, JavaScript must "cook" (render) the content.
🔹 In SSR, the server has already done the "cooking."

>Note-To Make SSR More Dynamic
    In a real-world SSR app, you can use JavaScript on the server (Node.js with Express) to generate dynamic content before sending the page.

    For example, if we modify server.js to generate HTML dynamically:

```
    const express = require("express");
    const app = express();
    const PORT = 3000;

    // Example of dynamic SSR rendering
    app.get("/", (req, res) => {
        const userName = "John Doe";  // Example dynamic data
        const htmlContent = `
            <!DOCTYPE html>
            <html lang="en">
            <head>
                <meta charset="UTF-8">
                <title>Server-Side Rendering Example</title>
            </head>
            <body>
                <h1>Welcome, ${userName}!</h1>
                <p>This page was rendered on the server.</p>
            </body>
            </html>
        `;
        res.send(htmlContent);
    });

    app.listen(PORT, () => {
        console.log(`Server is running at http://localhost:${PORT}`);
    });
```
>Why This is SSR?
    The server dynamically generates the final HTML.
    The browser just receives and displays the full page.
    No JavaScript runs on the client-side to fetch content.
    CSR Example for Comparison
    In CSR, the server sends only an empty structure, and JavaScript fetches & fills the content.


```
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Client-Side Rendering Example</title>
        <script defer src="script.js"></script>
    </head>
    <body>
        <h1 id="title">Loading...</h1>
    </body>
    </html>
    script.js (Filling the Content)
    javascript
    Copy
    Edit
    document.addEventListener("DOMContentLoaded", function () {
        setTimeout(() => {
            document.getElementById("title").innerText = "Welcome, John Doe!";
        }, 2000); // Simulating dynamic rendering
    });

```
>Why This is CSR?
    The server sends only an empty page.
    JavaScript fetches and fills the content dynamically.
