# ![Environment Variables - Concepts](./assets/hero.png)

**Learning Objective:** By the end of this lesson, students will understand the role and importance of environment variables in full-stack development.

## Understanding application environments

As a full-stack developer, your apps often involve working with external databases, servers, and authentication services. Your apps also need to understand the local environment they are operating in and take it into account. These components collectively form the context or the *environment* in which your applications operate. This environment encompasses all the external elements and services that interact with your app.

### Multiple environments

The environment an application runs in will likely vary depending on the context in which it is being run. Suppose we have an application that requires a database to store information.

The best practice would be to have two *environments*:

- **Development environment**: While developing and testing, the app would connect to a test database filled with dummy data for development purposes. This data can be modified or even deleted freely because it is not user-facing and, therefore, unimportant. This environment is commonly referred to as *dev*.
- **Production environment**: When the app is deployed to the internet, where users can interact with it, the app will connect to a different production database. Here, maintaining data integrity is crucial as real user data is involved. This environment is commonly referred to as *prod*.

You wouldn't want developers messing around with the data for actual users, as they might mess something up in the development process - impacting real users in detrimental ways.

Note that many apps may have more or different environments than these two - the scale and functionality of an app and the dev team working on a project will influence these decisions. The example above represents an appropriate baseline for any app.

> 📚 An application's *environment* is all the external factors that impact its operation in a given circumstance. It includes things like the configuration for an application (such as what database it should connect to). It could even include details like what network port the application should run on so that it can run alongside other applications. < tktk I'm not sure I like this last sentence, it could go.

## Environment variables

To manage these varying environments, we use ***environment variables***. They store specific data (like database URLs containing passwords) that change between environments. Collectively, these variables form the app's configuration or config.

### Why use environment variables?

#### 1. Separation of Concerns

The first main reason to use environment variables involves separating concerns between our app's code and how it's configured.

- Config varies with environments; source code generally does not.
- Using environment variables allows us to change settings within a config file without altering the rest of the codebase.

These points are important because they allow us to deploy an application and only change the environment variables to their new value; none of the code we've written changes. Not changing the code we've written is important because it allows us to use the same codebase for developing and deploying applications.

#### 2. Security

The other primary reason to use environment variables is that they help protect sensitive information (things like API keys, passwords, authentication credentials, etc.). You should never hardcode secrets like these into your code.

Environment variables safeguard sensitive data:

- API keys, passwords, and credentials are stored securely in a separate file.
- Avoid hardcoding secrets into source code, which risks exposure if pushed to repositories like `GitHub`.

## Example Scenario

The app example above mentioned that connecting to a database requires a password. If we were to push this password to GitHub as part of our codebase, anyone on the internet could read our password and act as an owner of our database!

The same goes for items like API keys. While this is not as much of a concern when using free services, as soon as we pay out of pocket for data storage or API calls, the consequences of accidentally uploading a secret become much more costly.

This is such a problem that GitHub generously employs a mechanism for scanning public repositories automatically for this type of security mistake called [secret scanning](https://docs.github.com/en/code-security/secret-scanning/about-secret-scanning). If you accidentally push details like this to a public GitHub repository, you'll likely receive an email and security warning on <github.com>.

To prevent this problem, we store our environment variables in a file called a `.env` and then tell Git to ignore that file when pushing our code to GitHub.
