# request.rest User Auth Example

```bash
GET http://localhost:3000/users

###

POST http://localhost:3000/users
Content-Type: application/json

{
"name": "Rick",
"password": "password"
}

###

POST http://localhost:3000/users/login
Content-Type: application/json

{
"name": "Rick",
"password": "password"
}
```

{collapsible="true" collapsed-title="request.rest"}

'###' denotes line separation