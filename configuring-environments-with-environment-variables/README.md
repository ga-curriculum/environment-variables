# ![Environment Variables - Configuring Environments with Environment Variables](./assets/hero.png)

tktk Hunter, could you update this hero? Also not wild about this name, if you have a suggestion here I'm all ears. I think I'd ideally name this **Environment Variables** but I refuse to have a microlesson with the same title as a module lol.

**Learning objective**: By the end of this lesson, students will understand the value of using environment variables to configure environments.

## Environment variables

To make use of the environment configuration in our code, we use ***environment variables***. They store specific data (like database URLs containing passwords) that may change between environments. Collectively, these variables are an app's configuration.

### Why use environment variables?

#### 1. Separation of Concerns

The main reason to use environment variables involves separating concerns between our app's code and how it's configured.

- Configuration varies with environments; source code generally does not.
- Using environment variables allows us to change settings within a config file without altering the rest of the codebase.

These points are important because they allow us to deploy an application and only change the environment variables to their new values; none of the code we've written changes. Not changing the code we've written is important because it allows us to use the same codebase for developing and deploying applications.

#### 2. Security

Environment variables also help protect sensitive information (API keys, passwords, authentication credentials, etc.). You should ***never*** hardcode secrets like these into your code. If you push hardcoded secrets to GitHub, they will be exposed publicly.

## Example Scenario

The app example above mentioned that connecting to a database requires a password. If we were to push this password to GitHub as part of our codebase, anyone on the internet could read our password and act as an owner of our database!

The same goes for items like API keys. While this is not as much of a concern when using free services, as soon as we pay out of pocket for data storage or API calls, the consequences of accidentally uploading a secret become much more costly.

This is such a problem that GitHub generously employs a mechanism for scanning public repositories automatically for this type of security mistake called [secret scanning](https://docs.github.com/en/code-security/secret-scanning/about-secret-scanning). If you accidentally push details like this to a public GitHub repository, you'll likely receive an email and security warning on [GitHub](https://github.com).

To prevent this problem, we store our environment variables in a file called a `.env` and then tell Git to ignore that file when pushing our code to GitHub.
