# Module Bundlers

### **What is a module bundler?**

In simple words, a module bundler is a tool whose task is to take multiple JS files and combine them into a single JS file along with the required libraries.

### **Why combine all JS files?**

In this era, all modern browsers support the Ecma script modules which means we can use import and export in our project and the browser will know how to handle that we only need to specify an entry point.

```javascript
export const name = "umair";
```

```javascript
import {name} from "./name.js";
console.log(name);
```

As modern browsers understand modules but it is not a suggested way to serve code to browsers because in order to use multiple JS we need to import all JS files in our script tag.

```xml
<script type="module" src="name.js"></script>
<script type="module" src="index.js"></script>
```

This code looks simple only two files but what happens if we use npm modules which have their dependency those dependencies will have their own dependency and the list goes on. So it will be inefficient to serve all those files to the browser. This will increase load time of our page by making a lot of requests.

And what if a user is using an old version of the browser? Do we need to write separate code for him?

No, this is where module bundlers are used to combine all those files in such a way that they can be understood by the browser. These are not just JS files a module bundler outputs an optimized bundle that contains all JS files, CSS files & assets like images, fonts etc.

### Key features of module bundlers

1. It helps developers to manage all of the dependency relationships.
    
2. It outputs code that is supported by all browsers whether they support ES modules or not.
    
3. It helps in optimizing code by removing comments, spaces, unused code etc.
    
4. It helps in optimizing the loading of assets like CSS and images.