# ![Environment Variables - Using Environment Variables in Node](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to tktk

## dotenv

[dotenv](https://www.npmjs.com/package/dotenv) is a popular module that allows us to load environment variables from a `.env` file in Node. These variables are stored as a key=value pair, and accessible on the `process.env` object. 

So, in our `.env` we could include: 

```yaml
SECRETPASSWORD=1234
```

And then within our code, we can access the value:

```javascript
process.env.SECRETPASSWORD // 1234
```

While this is cool on its own, remember that a `.env` file is largely used to keep secrets safe! Our 'SECRETPASSWORD' is still very visible if we were to push our code up to GitHub, it's just been moved into a different file. This is where `.gitignore` comes into play!

## gitignore, and protecting your secrets

A `.gitignore` file specifies intentionally untracked files to ignore. When we include our `.env` file in a `.gitignore`, we tell Git to ignore this file whenever we add, commit, and push code to GitHub.  

Now, our static code will always try to access `process.env.SECRETPASSWORD`, but each local machine that pulls our code down will need to supply their own SECRETPASSWORD variable in their own `.env` file. Our local secret is safe! 


## How to install and use
