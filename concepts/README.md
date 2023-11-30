# ![Environment Variables - Concepts](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to tktk

## What is an environment?

At the end of the day, even complex code boils down to a static series of logical rules and Boolean choices. 

Of course, nothing is ever that simple - when code is run, there are other factors to take into account. In Node, we'll frequently make use of external databases, servers, and authentication services in the projects we build. All of these things make up the context in which our apps run - that is to say, the **Environment** they exist in. 

The environment an application runs in can be variable! Let's imagine we have an Express app that requires a database to store information. 

When we are testing the app, we'll connect to a database server that is designated for testing. It will likely have a lot of incomplete data, and may need to be completely dropped from time to time. The deployed app, on the other hand, will connect to a different server - one maintained for actual users. 

The same application code will have to run in different environments, using different connection strings and passwords. When this is the case, we can store environment variables in a `.env` file and access them from our static codebase. 

When you have values that change based on an environment, they should go in `.env` files.

## Why use environment variables?

The other primary reason to use a `.env` file is that it protects our secrets (things like API keys, passwords, etc.). In the above example, we mentioned that connecting to a database requires a password. If we were to push this password to GitHub as part of our codebase, anyone could read our password and use our database for themselves! The same goes for things like API keys. While this is not as much of a concern when using free services, as soon as we are paying out of pocket for server space or API calls, the consequences for accidentally uploading a secret become much more severe. 

So, we definitely don't want bad actors to be able to access our secrets.

So, in summary - why use environment variables?

1. Security - the separation of these variables from our codebase allows us to 'hide' them from bad actors.

2. 




