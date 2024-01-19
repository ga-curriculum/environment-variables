# ![Environment Variables - Concepts](./assets/hero.png)

**Learning Objective:** By the end of this lesson, students will understand the role and importance of environment variables in full-stack development.

## Understanding application environments

As a full-stack developer, your projects will often involve working with external databases, servers, and authentication services. These components collectively form the context or the **Environment** in which your applications operate. This environment encompasses all the external elements and services that interact with your app.

### Multiple environments

The environment an application runs in is likely to vary between deployments. Let's imagine we have an `Express` application that requires a database to store information. 

Best practice would be to have two *environments*:

- **Development Environment:** While testing, the app connects to a test database filled with dummy data for development purposes.

- **Production Environment:** In a live setting, the app connects to a different, live users database. Here, maintaining data integrity is crucial as real user data is involved.

You wouldn't want developers messing around with the data for actual users, as they might mess something up in the process of development- impacting real users in detrimental ways.

### Environment variables

To manage these varying environments, we use ***environment variables***. They store specific data (like database URLs, passwords) that changes between environments. Collectively, these variables form the app's ***config***, short for configuration.

## Why use environment variables?

### 1. Separation of Concerns

The first main reason to use environment variables has to do with keeping a separation of concerns. Best practices dictate a clear separation between an *app's code* and its *config*:

- Config varies with environments, source code generally does not

- Using environment variables allows us to change settings within a config file without altering the rest of the codebase.

### 2. Security

The other primary reason to use environment variables is that it helps protect sensitive information (things like API keys, passwords, authentication credentials, etc.). You should never hardcode secrets like these into your code.

Environment variables safeguard sensitive data:

- API keys, passwords, and credentials are stored securely in a separate file
- Avoid hardcoding secrets into source code, which risks exposure if pushed to repositories like `GitHub`.

### Example Scenario

In the Express example above, we mentioned that connecting to a database requires a password. If we were to push this password to GitHub as part of our codebase, anyone could read our password and use our database!

The same goes for things like API keys. While this is not as much of a concern when using free services, as soon as we are paying out of pocket for data storage or API calls, the consequences for accidentally uploading a secret become much more costly.

**Solution:**

 To avoid this, we store our environment variables in a file called a `.env` and then tell GitHub to ignore that file when pushing our code.

