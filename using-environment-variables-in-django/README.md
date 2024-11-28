<h1>
  <span class="headline">Environment Variables</span>
  <span class="subhead">Using Environment Variables in Django</span>
</h1>

**Learning objective**: By the end of this lesson, students will be able to use and protect `.env` files in Django projects.

## Introduction to django-environ

Environment variables are crucial in Django applications, especially for managing sensitive data like API keys, database URLs, and secret keys. They help keep our secrets safe and separate from our source code.

`django-environ` is a package that allows Django to use environment variables, similar to how we used `dotenv` in Express. It's a convenient way to manage settings that differ between development and production, such as secret keys and database URLs.

### Step 1: Installing django-environ

To install `django-environ` for the first time, follow these steps:

1. **Install django-environ**: Open your terminal and run:

   ```bash
   pip3 install django-environ
   ```

2. **Check Installed Packages**: To see all installed Python packages, run:

   ```bash
   pip3 freeze
   ```

3. **Update requirements.txt**: Redirect the output of `pip3 freeze` to requirements.txt:

   ```bash
   pip3 freeze > requirements.txt
   ```

### Step 2: Setting up the .env file

1. **Create `.env` File**: In the same directory as your `settings.py`, create a `.env` file:

   ```bash
   touch .env
   ```

2. **Add Secrets**: Inside `.env`, add your secret variables:

   ```plaintext
   SECRET_KEY=your_secret_key_here
   ```

### Step 3: Integrating django-environ in settings.py

1. **Import and Initialize**: At the top of your `settings.py`, add:

   ```python
   import environ
   env = environ.Env()
   environ.Env.read_env()
   ```

   This code imports the `environ` module, initializes an environment instance, and reads your `.env` file.

2. **Access Secrets**: Whenever you need to access a secret, use:

   ```python
   env('SECRET_KEY')
   ```

   Replace `SECRET_KEY` with the corresponding key name from your `.env` file as needed.

### Step 4: Deployment considerations

When deploying your Django application (e.g., to Heroku), remember to set the same environment variables in your deployment environment. The values might differ from your local setup.
