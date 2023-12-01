# server.js User Auth Example

## Steps/Notes {collapsible="true" default-state="expanded"}

1. setup express

    1. `const express = require('express');`: pulls in express library
    2. `const app = express();`: instantiates the express class
    3. `app.listen(3000)`: server listens for traffic on port 3000
        1. you can also use a variable constant `PORT` and pass that in to `app.listen(PORT);` as well or save it in a
           .env file and pull that file in (but must install `npm i dotenv` to make this work)

2. create first route to test the server is working properly
3. create a [request.rest](request-rest-User-Auth-Example.md) file to test the routes
   in the editor

    1. you need to have [REST Client](https://marketplace.visualstudio.com/items?itemName=humao.rest-client) extension
       installed
    2. allows you to make REST requests to your api right inside vscode instead of using Postman or Insomnia

4. create route to create users
    1. this will contain all the logic to create user and hashed password
    2. since this app will need to accept json, need to add `app.use(express.json());`
    3. get user data from body **NOTE**: password is stored in plain text
    4. add to db
    5. send success back to user
5. require [brcypt](https://www.npmjs.com/package/bcrypt)
    1. create a salt
    2. use salt with password to create hashed password
    3. this is an async library
6. use [brcypt](https://www.npmjs.com/package/bcrypt) to hash password before storing in db
7. create route to login user
    1. locate user in db
    2. if no user send status of 400
    3. use [brcypt](https://www.npmjs.com/package/bcrypt) to compare user supplied password to hashed password stored in
       db.
    4. if match, log user in else return 'Not allowed'

```node
const express = require('express');
const app = express();
const bcrypt = require('bcrypt');

app.use(express.json());

// mock db
const users = [];

// first route
app.get('/users', (req, res) => {
    res.json(users);    // normally call db to get these
});

// **BAD EXAMPLE**
// create user and save clear text password
app.post('/users', (req, res) => {
    // user data from body of request - clear text password
    const user = { name: req.body.name, password: req.body.password };
    // add to mock db
    users.push(user);
    //send status back successfully done
    res.status(201).send(user);
});

// **GOOD EXAMPLE**
// create user and save hashed password
app.post('/users', async (req, res) => {
  try {
    const salt = await bcrypt.genSalt(); // nothing provided so default=10
    const hashedPassword = await bcrypt.hash(req.body.password, salt);

    // user data from body of request and hashedpassword
    const user = { name: req.body.name, password: hashedPassword };

    // add to mock db
    users.push(user);

    //send status back successfully done
    res.status(201).send(user);
  } catch (error) {
    res.status(500).send();
  }
});

// login user
app.post('/users/login', async (req, res) => {
  // look for user in mock db
  const user = users.find((user) => user.name === req.body.name);

  // if user does not exits
  if (user === null) {
    return res.status(400).send('Cannot find user');
  }

  // compare supplied password to stores hashed password
  try {
    if (await bcrypt.compare(req.body.password, user.password)) {
      res.send('Success');
    } else {
      res.send('Not allowed');
    }
  } catch (error) {
    res.status(500).send();
  }
});

app.listen(3000);
```

{collapsible="true" collapsed-title="server.js"}

<seealso>
[bcrypt](https://www.npmjs.com/package/bcrypt)
</seealso>
