---
name: Getting Started
---

# Getting Started

Let's get our first Isobel up and running.

The first step is to ensure you have node.js installed on your machine.

Ok, let's get this party started. First, create a new folder on your desktop called 'myIsobelApp' (or whatever you like). Then, open your text editor (we like Visual Studio Code), and open the 'myIsobelApp' folder within it.

Create a `package.json` file, and copy this code into it.

```json
{
  "name": "my-isobel-app",
  "version": "1.0.0",
  "description": "Look ma, I'm on the internet!",
  "main": "index.js",
  "scripts": {
    "start": "node index.js"
  },
  "author": "your name here"
}
```

Now. Let's install Isobel. Run the following snippit in your terminal to install

`yarn add @isobel/core @isobel/file-system @isobel/nasa`

Then, create an `index.js` file, and copy this code into it.

```javascript
const ISOBEL = require("@isobel/core");
const fileSystem = require("@isobel/file-system");
const nasa = require("@isobel/nasa");

// initialise
const Isobel = new ISOBEL({
  cache: fileSystem,
  endpoints: [
    {
      name: "nasa",
      func: nasa.fetchPhotoOfTheDay,
      interval: 24 * 60 * 60 * 1000; // 24 hours
    }
  ]
});

Isobel.start().catch(error => {
  console.error("Error:", error);
  process.exit(1);
});
```
