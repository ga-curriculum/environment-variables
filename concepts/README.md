# ![Environment Variables - Concepts](./assets/hero.png)

**Learning Objective:** By the end of this lesson, students will understand the role and importance of environments in full-stack development.

## Application environments

As a full-stack developer, your apps often work with external databases, servers, and authentication services. Your apps also need to understand the local *environment* they are operating in and take it into account. This environment encompasses all the external elements and services that interact with your app.

### Multiple environments

The environment an application runs in will likely vary depending on the context in which it operates. Suppose we have an application that requires a database to store information.

The best practice would be to have two *environments*:

- **Development environment**: While developing and testing, the app would connect to a test database filled with dummy data for development purposes. This data can be modified or even deleted freely because it is not user-facing and, therefore, unimportant. This environment is commonly referred to as ***dev***.
- **Production environment**: When the app is deployed to the internet, where users can interact with it, the app will connect to a different production database. Here, maintaining data integrity is crucial as real user data is involved. This environment is commonly referred to as ***prod***.

You wouldn't want developers messing around with the data for actual users, as they might mess something up in the development process - impacting real users in detrimental ways.

Note that many apps may have more or different environments than these two - the scale and functionality of an app and the dev team working on a project will influence these decisions. The example above represents an appropriate baseline for any app.

> 📚 An application's *environment* is all the external factors that impact its operation in a given circumstance. It includes things like the configuration for an application (such as what database it should connect to).
