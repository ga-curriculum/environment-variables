# ![Environment Variables - Using Environment Variables in Django](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will understand how to use and protect `.env` files in a Django application.

## Introduction to Environment Variables in Django

Environment variables play a crucial role in Django applications, especially for managing sensitive data like API keys, database URLs, and secret keys. They help keep our secrets safe and separate from our source code.

### Using `python-decouple`

While Django doesn't have a built-in tool like `dotenv` for Node, we can use a package like [`python-decouple`](https://pypi.org/project/python-decouple/) to manage environment variables.


First, install `python-decouple`:

```bash
pip install python-decouple
```

### Setting Up `.env` File

Create a `.env` file in your Django project's root directory:

```bash
touch .env
```

Inside this file, add your environment variables:

```plaintext
DJANGO_SECRET_KEY=mysecretkey
DJANGO_DEBUG=True
DATABASE_URL=sqlite:///mydatabase.db
```

> Note: Like `.env` in Node, `.env` in Django is a simple file with KEY=value pairs.

### Accessing Environment Variables in Django

The `settings.py` file is where you configure various settings and options for your Django project, including security settings, database configurations, installed apps, middleware, and more.

Import `Config` from `decouple` and use it to access environment variables:

```python
from decouple import Config

config = Config('.env')

SECRET_KEY = config('DJANGO_SECRET_KEY')
DEBUG = config('DJANGO_DEBUG', cast=bool)
DATABASES = {
    'default': config('DATABASE_URL', cast=db_url)
}
```

> `cast` is used to convert environment variable strings to Python data types.

### Default Values with `decouple`

`python-decouple` allows for default values if an environment variable isn't set:

```python
DEBUG = config('DJANGO_DEBUG', default=True, cast=bool)
```

### Running the Django Server

Start your Django server as usual:

```bash
python manage.py runserver
```

You'll see that it uses the environment variables from your `.env` file.

### Securing Secrets with `.gitignore`

To keep your secrets safe, include `.env` in your `.gitignore` file:

```plaintext
.env
```

This step ensures that sensitive data won't be pushed to public repositories.

Go ahead and push your code to GitHub. Your `.env` won't be visible, safeguarding your application's secrets.

### Note for Django Developers

It's crucial to manage environment variables effectively for a secure and efficient Django application. Using `python-decouple` with a `.env` file and `.gitignore` is an effective way to handle sensitive data and configurations across different environments in Django projects.
