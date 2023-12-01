# server.js JWT Example

Reference

- [NPM JWT Doc](https://www.npmjs.com/package/jsonwebtoken)

## Steps/Notes {collapsible="true" default-state="expanded"}

- `const express = require('express')` bring in the express library
- `const app = express()` setup (instantiate) the express server
- `app.listen(<PORT>)` needs to be the last line of code in `server.js` and at a minimum you need to pass in a port
  number
- setup authenticate with JWT
    - example would be so only certain users can have access to posts and not just everyone
    - `const jwt = require('jsonwebtoken')` bring in jwt library
    - `app.use(express.json)` since json will be passed into the server from login route, need to allow the server to be
      able to read the json that gets passed up to it from the body
    - `jwt.sign(obj, TOKEN_SECRET)` serialize the obj with a JWT
    - create a `ACCESS_TOKEN_SECRET` in the `.env` file
    - `require('dotenv').config()` load `.env` file
- create a middleware function to attach to what ever routes we want to protect
- attach `authenticateToken` middleware to all routes that need an authenticated user to access
    - `authHeader && authHeader.split(' ')[1]` checks for the presence of an `authHeader` and if there return the token
      portion of the authHeader array (`[BEARER JWT_TOKEN]`) after it is split otherwise returns undefined
    - `jwt.verify()` takes the token, SECRET and callback function
    - the callback function which takes in the error and serialized obj parameters
    - `next()` passes control on to the next piece of code whether that is another middleware or back to the main file
- `post.username === req.user.name` this will only add back the posts that belong to the authenticated user

```node
require('dotenv').config();

const express = require('express');
const jwt = require('jsonwebtoken');

const app = express();

app.use(express.json());

const posts = [
    {
        username: 'Kyle',
        title: 'Post 1'
    },
    {
        username: 'Jim',
        title: 'Post 2'
    }
];

app.get('/posts', authenticateToken,(req, res) => {
    res.json(posts.filter((post) => post.username === req.user.name));
});

// middleware to authenticate user
function authenticateToken(req, res, next) {
  const authHeader = req.headers['authorization'];

  const token = authHeader && authHeader.split(' ')[1];

  if (token === null) return res.sendStatus(401);

  jwt.verify(token, process.env.ACCESS_TOKEN_SECRET, (err, user) => {
    if (err) return res.sendStatus(403);

    req.user = user;
    next();
  });
}

app.listen(3000)
```

{collapsible="true" collapsed-title="server.js"}
