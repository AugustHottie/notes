# Markdown Notes - Flask Application

## Project Overview

**Markdown Notes** is a web-based note-taking application built with Flask. It allows users to create and manage notes using Markdown syntax, making it ideal for storing code snippets, personal notes, or any kind of text-based content.

---

## Prerequisites

Before you begin, ensure that you have the following installed:

- **Python 3.x**
- **Pipenv** for environment management
- **PostgreSQL** for database management
- **Docker** (if setting up PostgreSQL through Docker)

If you don't have PostgreSQL set up locally, you can refer to the [PostgreSQL Setup Guide](https://www.postgresql.org/docs/current/tutorial-install.html) to create a CentOS server and install PostgreSQL using Docker.

---

## Setting Up the Flask Application

### Step 1: Initialize the Project with Pipenv

To start, create a project folder and initialize a Python environment using Pipenv:

```bash
git clone https://github.com/AugustHottie/notes.git
cd notes
pipenv --python 3
```

### Step 2: Install Required Dependencies

Next, we need to install the necessary packages for Flask, database interactions, and migrations:

```bash
pipenv install Flask psycopg2-binary Flask-SQLAlchemy Flask-Migrate
```

This will install the following:
- `Flask`: The micro web framework we'll use for building the app.
- `Flask-SQLAlchemy`: A SQL toolkit and ORM for interacting with the PostgreSQL database.
- `Flask-Migrate`: A tool for handling database migrations.
- `psycopg2-binary`: PostgreSQL database adapter for Python.

### Step 3: Set Up the Basic Project Structure

To keep things organized, we'll set up the following basic structure:

```
notes/
├── Pipfile
├── Pipfile.lock
├── __init__.py    # Entry point of the application
├── config.py      # Database configuration and other settings
├── models.py      # Where we'll define our database models
├── /static        # Holds static assets like CSS, JavaScript for the app's front-end.
└── /templates     # Directory for HTML templates
```

### Creating the `notes` Database

Once PostgreSQL is installed and running, create the database by running:

```bash
sudo docker exec -i postgres psql postgres -U [POSTGRES_USER] -c "CREATE DATABASE notes;"
```

Replace `[POSTGRES_USER]` with your PostgreSQL username.

---

### Running Migrations

Migrations help us keep track of changes to the database schema. We'll use **Flask-Migrate** to manage database migrations.

```bash
    pipenv shell
    flask db init
    flask db migrate -m "Initial migration."
    flask db upgrade
```

This will create the `migrations` folder and apply the initial migration, creating the `User` and `Note` tables in the `notes` database.

---

## Running the Application

Once everything is set up, you can run the Flask application locally:

```bash
pipenv shell
flask run
```

Visit `http://127.0.0.1:5000/` in your browser to see the app in action!

---

**Create a New Note**:

   Navigate to `http://127.0.0.1:5000/notes_create` to create a new Markdown-based note.

**View All Notes**:

You can view all saved notes by going to `http://127.0.0.1:5000/notes`.

![image](https://github.com/user-attachments/assets/c6d70f97-0014-4a90-89c5-edbd503fab0c)

---


## Contributing

I'm open to contributions! If you have ideas for new features or improvements, feel free to submit a pull request.

### Steps to Contribute:

1. Fork this repository.
2. Create a feature branch: `git checkout -b feature/new-feature`.
3. Commit your changes: `git commit -m 'Add new feature'`.
4. Push to the branch: `git push origin feature/new-feature`.
5. Submit a pull request.

## Additional Notes

### Flask Documentation
You can find the official Flask documentation [here](http://flask.pocoo.org/).

### Pipenv Documentation
For more information on managing Python environments with Pipenv, visit [Pipenv Docs](https://pipenv.readthedocs.io/en/latest/).

---
