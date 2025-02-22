## Express responde methods
**List of express response methods below with code**

 Express provides several methods similar to res.send(), each with slight differences in behavior. Here are some commonly used alternatives:

1. res.json()
    * Sends a JSON response instead of a plain text/string response.
    * Automatically sets Content-Type: application/json.

    * `res.json({ message: "This item has been saved to the database" });`

2. res.sendFile()
    * Sends a file as a response.
    * Example:
    * `res.sendFile(__dirname + "/index.html");`

3. res.status().send() 
    * Allows setting a custom HTTP status code before sending a response.
    * Example:
    * `res.status(201).send("Item successfully created");*`

4. res.end()
    * Ends the response without sending any data.
    * Example:
    * `res.end();`

5. res.redirect()
    * Redirects the client to a different URL.
    * Example:
    * `res.redirect('/home');`
  
>NOTE->File can be send using .end method as well but it is not recocmended because of two resons

![Code snippet]()

1. When we sne a Html file the browser need to know that it is a html file so which need to be done   manually well sometime it works without it but not rrecomended
2. NO automatic content length so page have problem in loading
3. res.end(home); sends the entire file at once, which can slow down performance.

**Difference between .send() and .senfile()**

1. send()is ideal for short and static serving also preloading
     ```
        const fs = require('fs');
            const path = require('path');
            const express = require('express');

            const app = express();

            // ✅ Preloading the file: Reading it once when the server starts
            const home = fs.readFileSync(path.join(__dirname, 'static', 'f.html'), 'utf8');

            app.get('/', (req, res) => {
                res.status(200).send(home); // Sending preloaded file content
            });

            app.listen(3000, () => console.log("Server running on port 3000"));
    ```

    > How This Works
    The file f.html is read into memory when the server starts, so it's available instantly when a request is made.
    When a client requests /, Express immediately sends the stored content (home) without reading the file again.
    Advantages of Preloading
    Faster Response → No need to read the file from disk on each request.
    Useful for Small Files → Works well for small static content (like small HTMLfiles).



2. If the file might change or is large, it's better to read it only when requested:
    ```
        app.get('/', (req, res) => {
            res.sendFile(path.join(__dirname, 'static', 'f.html'));
        });
    ```
    >✅ Reads the file each time it's requested.
        ✅ Efficient for large files (it streams data instead of keeping it in memory).
        ✅ Automatically sets correct headers like Content-Type.