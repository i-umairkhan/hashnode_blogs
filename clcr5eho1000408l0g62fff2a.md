# Introduction - Module Bundlers

## **What is a module bundler?**

Module bundlers are tools that help in managing dependencies in JavaScript applications. They take the multiple JavaScript files in an application and combine them into a single file (bundle), making it easier to load the application in a browser. This also helps in reducing the number of network requests required to load an application, leading to improved performance.

A module bundler operates on the assumption that a JavaScript application can be organized into smaller, reusable modules. Each module exports variables, functions or objects that other modules can use in the application. The module bundler takes these modules and builds the relationships between them, creating a dependency graph. Based on the graph, it generates a single file (bundle) that contains all the necessary code for the application to run.

Some of the popular module bundlers are:

* Webpack
    
* Rollup
    
* Parcel
    
* Browserify
    

Module bundlers also come with various plugins and configuration options that allow you to perform various tasks such as transpiring code, handling CSS files, etc.

## Why use module bundlers?

1. Code organization: Module bundlers allow you to organize your code into smaller, reusable units called modules. Each module can export and import functions, objects, and other values from other modules, making it easier to structure your code and reuse code across your application.
    
2. Dependency management: Module bundlers allow you to manage the dependencies between different modules in your application. When you import a module, the bundler will automatically include the dependencies that the module needs in the final bundle.
    
3. Improved performance: Module bundlers can optimize your code for faster loading and execution in a web browser. They can perform optimizations such as tree shaking, which removes unused code, and code splitting, which allows you to load only the code that is needed for a specific part of your application.
    
4. Cross-browser compatibility: Module bundlers can also help with cross-browser compatibility by transpiling your code to an older version of JavaScript that is compatible with older browsers.
    
5. Asset management: Module bundlers can also help manage assets like images, fonts, and stylesheets, by allowing you to import these assets into your JavaScript code and bundle them together with your code.
    

In summary, module bundlers are a key tool for building modern JavaScript applications, providing a way to organize, manage, and optimize your code, as well as manage dependencies and assets.

## **Why combine all JS files?**

In this era, all modern browsers support the Ecma script modules which means we can use import and export in our project and the browser will know how to handle that, we only need to specify an entry point.

```javascript
export const name = "umair";
```

```javascript
import {name} from "./name.js";
console.log(name);
```

Modern browsers understand modules but it is not a suggested way to serve code to browsers because to use multiple JS we need to import all JS files in our HTML script tag.

```xml
<script type="module" src="name.js"></script>
<script type="module" src="index.js"></script>
```

This code looks simple only two files but what happens if we use npm modules that have their dependency those dependencies will have their dependence and the list goes on. So it will be inefficient to serve all those files to the browser. This will increase the load time of our page by making a lot of requests.

And what if a user is using an old version of the browser? Do we need to write separate code for him?

No, this is where module bundlers are used to combine all those files in such a way that they can be understood by the browser. These are not just JS files a module bundler outputs an optimized bundle that contains all JS files, CSS files & assets like images, fonts etc.

## How module bundlers work.

Here's a simple example to illustrate how a module bundler works.

Let's say you have two JavaScript files, `math.js` and `app.js`:

```javascript
// math.js 
export function add(a, b) { 
    return a + b; 
}

// app.js
import { add } from './math.js'; 
console.log(add(2, 3));
```

In this example, `app.js` is dependent on `math.js` as it is importing the `add` function from it. A module bundler would take these two files and bundle them into a single file, which can be used in a browser or any other JavaScript environment. The bundled file would look something like this:

```javascript
(function() {
  function add(a, b) {
    return a + b;
  }

  console.log(add(2, 3));
})();
```

Note that the module bundler has removed the explicit imports and exports and instead used an anonymous closure to create a self-contained bundle that can be executed in any JavaScript environment. This is just a simple example, but in real-world applications, the bundle would contain many more dependencies and be much larger. The module bundler takes care of managing these dependencies and generating a single file that can be easily used in a browser or any other JavaScript environment.

## Commonly used Module bundlers.

1. Webpack: Webpack is one of the most popular module bundlers for JavaScript applications. It is highly configurable and has a large number of plugins and loaders available, which makes it suitable for use in a wide range of applications. Webpack is also highly performant and can be used to build large and complex applications.
    
2. Rollup: Rollup is another popular module bundler that is focused on performance and outputs small, optimized bundles. It is particularly well-suited for library authors who want to publish their libraries as modular, easy-to-use packages. Rollup also supports tree-shaking, which helps reduce the size of the final bundle by removing unused code.
    
3. Parcel: Parcel is a relatively new module bundler that is focused on simplicity and ease of use. It has a fast development setup time and requires minimal configuration, making it a good choice for small to medium-sized projects. It also has a fast build time and is capable of hot module reloading, which allows you to see changes in your application immediately without having to reload the entire page.
    
4. Browserify: Browserify is one of the oldest module bundlers for JavaScript and was one of the first tools to allow using CommonJS modules in the browser. It is highly modular and has a large number of plugins available, making it suitable for use in a wide range of applications. However, it is not as performant as some of the other module bundlers and may not be the best choice for large and complex applications.
    
5. Vite: Vite is a relatively new module bundler that is focused on speed and efficient development. It was designed with modern JavaScript and web development in mind and aims to provide a fast and efficient development experience for JavaScript applications.
    
    One of the key features of Vite is that it performs all bundling in the background, allowing you to see your changes immediately in the browser without having to wait for a build to finish. This speeds up development and makes it easier to quickly iterate on your application.
    

Each of these module bundlers has its strengths and weaknesses, and the best choice will depend on the specific requirements of your project. It is always a good idea to consider your needs carefully and try out a few different tools before making a final decision.