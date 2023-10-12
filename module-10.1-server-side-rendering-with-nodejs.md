### Module 10.1: Server-Side Rendering (SSR) with Node.js

**Server-Side Rendering (SSR)** is a powerful technique in web development that involves rendering web pages on the server, sending the fully rendered HTML to the client, and then enhancing it with client-side interactivity. SSR offers several benefits, including improved performance, search engine optimization (SEO), and a faster initial page load.

In this module, we'll explore the concept of SSR and how to implement it using **Node.js**, a popular runtime for building server-side applications. We'll also take a look at some examples to better understand the process.

#### Key Concepts:
1. **Server-Side Rendering (SSR):** Rendering web pages on the server before sending them to the client's browser.

2. **React and Next.js:** The example in this module will demonstrate SSR using React and the Next.js framework.

3. **SEO Benefits:** SSR can improve search engine rankings as search engines can easily crawl and index server-rendered content.

4. **Performance Improvements:** Initial page load is faster because the server provides the fully rendered HTML.

#### Example: Implementing SSR with Node.js and Next.js

In this example, we'll create a simple SSR web application using Node.js and Next.js. Next.js is a popular framework that makes it easy to build server-rendered React applications.

1. **Initialize a New Project:**

   First, create a new directory for your project and navigate to it in your terminal.

   ```bash
   mkdir my-ssr-app
   cd my-ssr-app
   ```

2. **Initialize a Node.js Project:**

   Initialize a new Node.js project using npm.

   ```bash
   npm init -y
   ```

3. **Install Dependencies:**

   Install Next.js and React, which we'll use for building our SSR app.

   ```bash
   npm install next react react-dom
   ```

4. **Create Pages:**

   In the project directory, create a `pages` directory, and inside it, create an `index.js` file. This file will be the entry point for our application.

   ```javascript
   // pages/index.js

   const HomePage = () => {
     return <div>Welcome to my SSR app!</div>;
   };

   export default HomePage;
   ```

5. **Create a Custom Server:**

   To enable server-side rendering, we need to create a custom server using Next.js. In the root directory of your project, create a `server.js` file.

   ```javascript
   // server.js

   const express = require('express');
   const next = require('next');

   const dev = process.env.NODE_ENV !== 'production';
   const app = next({ dev });
   const handle = app.getRequestHandler();

   app.prepare().then(() => {
     const server = express();

     server.get('*', (req, res) => {
       return handle(req, res);
     });

     server.listen(3000, (err) => {
       if (err) throw err;
       console.log('> Ready on http://localhost:3000');
     });
   });
   ```

6. **Update `package.json` Scripts:**

   In your `package.json` file, add the following scripts for starting your custom server.

   ```json
   "scripts": {
     "dev": "node server.js"
   }
   ```

7. **Start the SSR App:**

   Start your SSR app by running:

   ```bash
   npm run dev
   ```

   Your SSR app should now be running on `http://localhost:3000`, and you can see the server-rendered content.

This is a basic example of how to implement Server-Side Rendering (SSR) using Node.js and Next.js. In a real-world scenario, you would build more complex pages and leverage the SEO and performance benefits that SSR offers.

Server-Side Rendering is a valuable technique, especially when you want your web applications to have good SEO performance and fast initial page loads. It's a skill that every advanced web developer should have in their toolkit.
