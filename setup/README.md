# ![Environment Variables - Setup](./assets/hero.png)

## Setup

Open your Terminal application and navigate to your `~/code/ga/lectures` directory:

```bash
cd ~/code/ga/lectures
```

Make a new directory called `environment-variables`, then enter this directory:

```bash
mkdir environment-variables
cd environment-variables
```

-- tktk connect git -- 

Then, create a `server.js` file. This file will hold your work for this lecture:

```bash
touch server.js
```

With the file created, open the contents of the directory in VS Code:

```bash
code .
```

In the terminal, create a `package.json` with all of the default settings by running the following command:

```bash
npm init -y
```

Next, we're going to add `Express` to our project: 

```bash
npm i express
```

In `server.js`, add the following starter code: 

```javascript
const express = require('express')
const app = express()

app.get('/', (req, res) => {
  res.send('Server is running')
})

app.listen(3000, () => {
  console.log('Listening on port 3000')
})
```

- Use `nodemon` to execute the `server.js` file by using this command in your terminal:

```bash
nodemon
```

Visit [localhost:3000](http://localhost:3000/) to make sure you did everything correctly.
