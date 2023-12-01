# ![Environment Variables - Using Environment Variables in Node](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to tktk

## dotenv

[dotenv](https://www.npmjs.com/package/dotenv) is a popular module that allows us to load environment variables from a `.env` file in Node. These variables are stored as a key=value pair, and accessible on the `process.env` object. 

Let's install dotenv: 

```bash
npm i dotenv
```

Next, to make use of it, we'll need to import the module. At the very top of `server.js`, add the following: 

```javascript
require('dotenv').config()
```

Finally, let's create our `.env` file. `dotenv` will look for this file in the root directory of your project, so we'll add it there: 

```bash
touch .env
```

Inside this `.env`, we can add variables. By convention, environment variables are written in all caps, with underscores separating multiple words. This helps to differentiate them from other variables. 

So, our environment variables will follow the following convention: 

```yaml
PORT=5000
SECRET_PASSWORD=1234
```

> Note that .env files are not JavaScript files, they're instead written in YAML. As such, every value is treated as a string, and we omit quotes. 

And then within our code, we can access the values:

```javascript
require('dotenv').config()
const express = require('express')
const app = express()

app.get('/', (req, res) => {
  res.send('Server is running!')
})

// add the following: 
const port = process.env.PORT ? process.env.PORT : '3000';

//adjust the following: 
app.listen(port, () => {
  console.log(`The express app is ready on port ${port}! Your secret is ${process.env.SECRET_PASSWORD}`);
});
```

The line
```javascript
const port = process.env.PORT ? process.env.PORT : '3000';
```
uses a ternary operator, and is a condensed way of expressing:
```javascript
// Create a new variable named 'port'
let port;
// If process.env.PORT has a defined value
if(process.env.PORT){
  // reassign port to this value
  port = process.env.PORT
} else {
  // otherwise, set port to the default value of '3000'
  port = '3000'
}
```

Run `nodemon`, and check out the `console.log()` in your terminal. 

You might be thinking "hold on, if most servers are using `.env` files, couldn't a bad actor just `console.log()` `process.env` and steal secrets that way?

Luckily, no - while Node understands environment variables through the use of tools like `dotenv`, the browser itself does not. Try to `console.log()` `process.env` in the browser, and you'll get a reference error - it has no idea what `process` is! As long as your secrets are in an `.env` file on the server side, they're safe. 

> You should not use environment variables to hold secrets in client side code - everything in client side code is public! 


## gitignore, and protecting your secrets

At this stage, our secrets are still very visible if we were to push our code up to GitHub, they've just been moved into a different file. This is where `.gitignore` comes into play!

A [`.gitignore`](https://git-scm.com/docs/gitignore) file specifies intentionally untracked files to ignore. When we include our `.env` file in a `.gitignore`, we tell Git to ignore this file whenever we add, commit, and push code to GitHub. 

```bash
touch .gitignore
```

In `.gitignore`, add the following: 

```plaintext
.env
```

Now, our secrets are not being uploaded to the internet for everyone to see! 

Go ahead and add, commit, and push your code to GitHub. Once you're done, check the repo. You should see your server file, but not the `.env`.

Our static code will always try to access `process.env.PORT` and `process.env.SECRET_PASSWORD`, but each local machine that pulls our code down will need to supply their own 'PORT' and 'SECRET_PASSWORD' variables, in their own `.env` file. Our local secrets are safe! 
