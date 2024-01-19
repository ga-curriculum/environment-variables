# ![Environment Variables - Using Environment Variables in Node](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to use and protect `.env` files. 

## Introduction to dotenv

[dotenv](https://www.npmjs.com/package/dotenv) is a popular Node module that loads environment variables from a `.env` file. This method is widely used for managing sensitive data like API keys and database URLs.

### Installing dotenv

First, we need to add `dotenv` to our project:

```bash
npm i dotenv
```

### Importing dotenv

Next, to make use of it, we'll need to import the module. Add this line at the very top of `server.js`:

```javascript
require('dotenv').config()
```

### Creating a `.env` file

Finally, create a `.env` file in your project's *root directory*. The `dotenv` package looks for it there by default: 

```bash
touch .env
```

Inside this `.env`, define your variables. By convention, environment variables are written in all caps, with underscores separating multiple words. This helps to differentiate them from other variables. 

Enter the following in your `.env` file: 

```plaintext
PORT=5000
SECRET_PASSWORD=1234
```

> Note that `.env` files are not JavaScript files. They are simply a set of KEY=value pairs where every value is treated as a string. We omit quotes around the values, and there is no `let` or `const` used when defining the keys.

### Accessing environment variables

The `dotenv` package creates a `process.env` object which contains properties that match the variables in our `.env` file. These variables are available in Node.js as `process.env.VARIABLE_NAME`. 

And then within our code, we can access the values:

```javascript
require('dotenv').config()
const express = require('express')
const app = express()

app.get('/', (req, res) => {
  res.send('Server is running!')
})

// add the following: 
const port = process.env.PORT || '3000';

// adjust the following: 
app.listen(port, () => {
  console.log(`The express app is ready on port ${port}! Your secret is ${process.env.SECRET_PASSWORD}`);
});
```

### Using the || operator for default values

Let's take a closer look at this interesting line of code:

```javascript
const port = process.env.PORT || '3000';
```

1) The code first checks if `process.env.PORT` is defined (if the `PORT` environment variable is set in the `.env`). If it's set, its value is assigned to the port variable. 

2) If `process.env.PORT` is not defined (which could be the case in a local development environment), the code falls back to using `'3000'` as the default port number.

> In other words "set this value to process.env.PORT OR 3000 if that doesn't exist"


### Run the server

Run `nodemon`, and check out the `console.log()` in your terminal.

> If everything was done correctly, you'll need to navigate to localhost:5000 now - remember, we changed the port! 

You should see it log out 'The express app is ready on port 5000! Your secret is 1234'. 

You might be thinking "hold on, if most servers are using `.env` files, couldn't a bad actor just `console.log()` `process.env` and steal secrets that way?

Thankfully, no - while Node understands environment variables through the use of tools like `dotenv`, the browser itself does not. Try to `console.log()` `process.env` in the browser, and you'll get a reference error - it has no idea what `process` is! As long as your secrets are in an `.env` file on the server side, they're safe! 


## Protecting secrets with `.gitignore`

At this stage, our secrets are still very visible if we were to push our code up to GitHub, they've just been moved into a different file. This is where `.gitignore` comes into play!

A [`.gitignore`](https://git-scm.com/docs/gitignore) file specifies intentionally untracked files to ignore. When we include our `.env` file in a `.gitignore`, we tell Git to ignore this file whenever we add, commit, and push code to GitHub. 

```bash
touch .gitignore
```

In `.gitignore`, add the following: 

```plaintext
.env
```

Go ahead and `add`, `commit`, and `push` your code to GitHub. Once you're done, check the repo. You should see your server file, but not the `.env`. 

Anyone cloning our code must create their own `.env` with specific `'PORT'` and `'SECRET_PASSWORD'` values. This approach ensures that sensitive information remains secure and our local secrets are safe! 

