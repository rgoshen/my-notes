# Python

**incomplete**

[![python-logo](python-logo.png)](https://www.python.org/)

## Introduction to Python Programming Language {collapsible="true" default-state="expanded"}

Python is a high-level, versatile programming language acclaimed for its readability and straightforward syntax. Ideal
for beginners and powerful enough for seasoned programmers, Python is widely used in diverse fields.

### What is Python?

- **High-Level Language**: Python abstracts many details of the computer's operation, focusing on readability and
  simplicity.
- **Interpreted Language**: Python code is executed line by line, making debugging easier and suitable for rapid
  prototyping.
- **Dynamically Typed**: Python does not require explicit declaration of variables before using them.

### Why Choose Python?

#### Readability and Simplicity

- Python emphasizes readability, which makes the code easier to understand and maintain.
- Its syntax is simple and concise, often requiring fewer lines of code than other languages.

#### Versatility

- Python is used in web development, data science, artificial intelligence, scientific computing, and automation.
- It's a general-purpose language, suitable for a wide range of applications.

#### Large Community and Libraries

- Python has a robust and active community, offering extensive support and resources.
- A vast array of libraries and frameworks are available, enhancing Python's functionality in various domains.

### Getting Started with Python

#### Installation

- Python can be installed from the official website: [python.org](https://www.python.org/).
- It comes with a built-in IDE (Integrated Development Environment) called IDLE.

#### Writing Your First Python Program

```python
# This is a simple Python script

print("Hello, World!")
```

- This script uses the `print` function to output "Hello, World!" – a traditional way to start learning a new
  programming language.

### Key Python Concepts

- **Variables**: Store data values.
- **Data Types**: Include integers, floats, strings, lists, tuples, and dictionaries.
- **Control Structures**: if statements, for and while loops.
- **Functions**: Blocks of reusable code.
- **Classes/Objects**: Python is an Object-Oriented Programming (OOP) language.

### Python Resources

- **Official Documentation**: Comprehensive guide to Python's features and libraries.
- **Online Tutorials and Courses**: Websites like Codecademy, Coursera, and Udemy offer Python programming courses.
- **Community Forums**: Platforms like Stack Overflow provide a place to discuss and solve programming issues.

## Misc {collapsible="true" default-state="expanded"}

### Create a virtual environment

```bash
python -m venv venv    # create
source venv/bin/activate    # linux/macos
source venv/scripts/activate    # windows
pip freeze > requirements.txt    # create
pip install -r requirements.txt # install
deactivate    # stop
```

if you do not want to use `venv`, you can do this:

```bash
python -m venv /path/to_folder/<env_name>
source /path/to_folder/<env_name>/bin[source]/activate
```

### Setup [pyenv](https://github.com/pyenv/pyenv) for a project

- Steps to install [pyenv](https://github.com/pyenv/pyenv)
- [commands](https://github.com/pyenv/pyenv/blob/master/COMMANDS.md)

```bash
pyenv install --list    # see which are available
pyenv install <version>
pyenv global <version>    # to change the global version
cd <project-folder>
pyenv local <python-version>    # change the local version
python --version    # check version
python -m venv <env-name>
source venv/bin/activate    # for macos and Linux
source venv\scripts\activate    # for windows
venv\scripts\activate        # for powersehll
```

## Packages {collapsible="true" default-state="expanded"}

- API Requests - `pip install requests`
- BCrypt - `pip install bcrypt`
- Bootstrap Flask - `pip install bootstrap-flask`
- Flask = `pip install flask`
- Flask BCrypt - `pip install flask_bcrypt`
- Flask Debug Toolbar = `pip install flask-debugtoolbar`
    - then `flask.debugtoolbar import DebugToolbarExtensions`
- Flask SQLAlchemy - `pip install flask-sqlalchemy`
- Flask WTForms - `pip install flask-wtf`
    - then `from flask_wtf import FlaskForm`
    - also `from wtforms.validators import [validator]`
- Gunicorn - `pip install gunicorn`
- Interactive Python - `pip install ipython`
- Jinja2[^1] - `pip install jinja2`
- SQLAlchemy - `pip install psycopg2-binary

## Conclusion {collapsible="true" default-state="expanded"}

Python stands out as a language that is easy to learn yet powerful enough to handle complex tasks. Its simplicity, along
with its powerful libraries and supportive community, makes Python an excellent choice for both beginners and
experienced developers.

[^1]: normally installs when flask is installed

<seealso>
[![Python](https://img.shields.io/badge/Docs-python-3670A0?style=flat&logo=python&logoColor=ffdd54)](https://docs.python.org/3/) |
[Pip Docs](https://pip.pypa.io/en/stable/) |
[![Python](https://img.shields.io/badge/pypi-3775A9?style=flat&logo=pypi&logoColor=ffdd54)](https://pypi.org/) |
[Python Version Manager](https://github.com/pyenv/pyenv)
</seealso>
