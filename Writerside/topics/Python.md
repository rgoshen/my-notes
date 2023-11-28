# Python Cheatsheet

## Setup Virtual Environment {collapsible="true" default-state="expanded"}

```bash
cd <project-folder>
python3 -m venv <venv_name>
source venv_name/bin/activate # macos and linux only
pip3 freeze # list of installed Packages
pip3 freeze > requirements.txt # save list of installed packaged to requirements.txt
deactivate # deactivates virtual environment
```

## Recreate Virtual Environment {collapsible="true" default-state="expanded"}

```bash
git clone <url>
cd <project -folder>
python3 -m venv <venv_name>
source venv_name/bin/activate # macos and linux only
pip3 install -r requirements.txt
deactivate # deactivates virtual environment
```

## Run Python Programs {collapsible="true" default-state="expanded"}

- cli: `python3 <file.py>`
- iPython: `% run <file.py>`

## Run tests

- doctests: `python3 -m doctest -v <file.test.py>`
- unittests: `python3 -m unittest`

[//]: # (TODO: resolve link)
[Testing](../testing/python/python.testing.md) for more options on testing

## Run Flask Apps {collapsible="true" default-state="expanded"}

```bash
flask run
```

### Basic Flask App Template

```python
from flask import Flask, request

app = Flask(__name__)

app.config['SECRET_KEY'] = 'some secret key'

@app.route('/')
def home():
  return 'This is the home page.'
```

- flask.request allows the app to handle GET & POST requests
- `app = Flask(__name__)` is required, Flask needs to know what module is scan for routes
    - app is the name of the actual main python file. (i.e. app.py)

> **NOTE:**
>
> for app building you should make sure your flask environment is running in **development** mode. This will allow for
> debugging.
>
> `export FLASK_ENV=development`

## Generate a Secret Key {collapsible="true" default-state="expanded"}

```bash
os.urandom(<int>).hex()
```

or

```bash
os.urandom(<int>)
```

