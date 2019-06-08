# ISOBEL 🐶

Welcome!
Isobel is beginner-friendly NODE.js framework for caching data in API responses, so it can be used on your website or in other apps.

Services are API endpoints that Jarvis will request from. A great example is Twitter, which gets the latest posrts from your Twitter feed. Isobel includes a bunch of premade services, but you can also create your own.

Here is a minumum implementation of Isobel.

```javascript
const ISOBEL = require("@isobel/core");
const fileSystem = require("@isobel/file-system");
const nasa = require("@isobel/nasa");

const hours = n => n * 60 * 60 * 1000;

// initialise
const Isobel = new ISOBEL({
  port: 3000,
  cache: fileSystem,
  endpoints: [
    {
      name: "nasa",
      func: nasa.fetchPhotoOfTheDay, // gets the NASA photo of the day
      interval: hours(24)
    }
  ]
});

Isobel.start();

Isobel.app.listen(err => {
  if (err) console.error(err);
  console.log("⚙️ Starting caching");
});
```
