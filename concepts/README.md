# ![Environment Variables - Concepts](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to explain the importance of environment variables. 

## What is an environment?

At the end of the day, even complex code boils down to a static series of logical rules and Boolean choices. 

Of course, nothing is ever that simple - when code is run, there are external factors to take into account. In Node, we'll frequently make use of external databases, servers, and authentication services in the projects we build. All of these things make up the context in which our apps run - that is to say, the **Environment** they exist in. 

The environment an application runs in is likely to vary between deployments. Let's imagine we have an Express app that requires a database to store information. 

When we are testing the app, we'll connect to a database server that is designated for testing. In this developer environment, the database will likely have a lot of incomplete data, and may need to be completely dropped from time to time. The deployed app, on the other hand, will connect to a different server - one maintained for actual users. 

The same application code will have to run in different environments, using different connection strings and passwords. As a result, these variables would make up the app's __config__ (anything likely to change or vary between deployments).


## Why use environment variables?

The first main reason to use environment variables has to do with keeping a separation of concerns. It's widely considered best practice to keep separation between the code itself and its config - again, config will vary substantially across deployments, whereas code itself should not. 

Storing config in environment variables means that we can easily change variables between deployments without actually touching any of our code itself! 

The other primary reason to use a `.env` file is that it helps protect sensitive information (things like API keys, passwords, authentication credentials, etc.). You should never hardcode secrets like these into your code.

In the above example, we mentioned that connecting to a database requires a password. If we were to push this password to GitHub as part of our codebase, anyone could read our password and use our database for themselves! The same goes for things like API keys. While this is not as much of a concern when using free services, as soon as we are paying out of pocket for server space or API calls, the consequences for accidentally uploading a secret become much more costly. 

So, we definitely don't want bad actors to be able to access our secrets.
Fortunately, we can tell GitHub to ignore our `.env` file when pushing our code, keeping our environment variables safe and local. 





