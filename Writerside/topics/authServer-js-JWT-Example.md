# authServer.js JWT Example

1. create a function to generate an access token and add expiration date to it (usually 10-15 mins)
2. create a refresh token and return to user inside login route
3. create a new post route to issue new access tokens
    - check to make token was sent in body fo request
    - check to see if token is already been issued
    - verify if token is good and if good generate new access token
4. create a route to delete refresh tokens
    - upon logout delete user refresh token from database

> **NOTE:** normally you store the refresh token in some sort of database, but for this example, we will store it
>
> locally in authServer.js

```Javascript
require('dotenv').config();

const express = require('express');
const jwt = require('jsonwebtoken');

const app = express();

app.use(express.json());

let refreshTokens = [];

app.post('/login', (req, res) => {
  // Authenticate user

  const username = req.body.username;
  const user = { name: username };

  const accessToken = generateAccessToken(user);
  const refreshToken = jwt.sign(user, process.env.REFRESH_TOKEN_SECRET);

  refreshTokens.push(refreshToken);

  return res.json({ accessToken: accessToken, refreshToken: refreshToken });
} );

app.post('/logout', (req, res) => {
  refreshTokens = refreshTokens.filter((token) => token !== req.body.token);
  res.sendStatus(204);
});

app.post('/token', (req, res) => {
  const refreshToken = req.body.token;

  if (refreshToken === null) return res.sendStatus(401);
  if (!refreshTokens.includes(refreshToken)) return res.sendStatus(403);

  jwt.verify(refreshToken, process.env.REFRESH_TOKEN_SECRET, (err, user) => {
    if (err) return res.sendStatus(403);
    const accessToken = generateAccessToken({ name: user.name });
    res.json({ accessToken: accessToken });
  });
});

function generateAccessToken(user) {
  return jwt.sign(user, process.env.ACCESS_TOKEN_SECRET, { expiresIn: '15s' });
}

app.listen(4000)
```

{collapsible="true" collapsed-title="authServer.js"}