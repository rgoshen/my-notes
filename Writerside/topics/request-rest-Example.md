# Request.rest Example

```bash
GET http://localhost:3000/posts Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJuYW1lIjoiSmltIiwiaWF0IjoxNjQyOTA4NzE3LCJleHAiOjE2NDI5MDg3MzJ9.xutbIjvfjsJksXpkZGpGBjJ_6ga7mDboA9voHDgki8w

###

POST http://localhost:4000/login Content-Type: application/json

{
"username":"Jim"
}

###

POST http://localhost:4000/token Content-Type: application/json

{
"token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJuYW1lIjoiSmltIiwiaWF0IjoxNjQyOTA4NzU2fQ.X9DoSFp3tv4WOJhSKOAzf8qNyalXYeXHwqSGAAUALm0"
}

###

POST http://localhost:4000/logout Content-Type: application/json

{
"token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJuYW1lIjoiSmltIiwiaWF0IjoxNjQyOTA4NzU2fQ.X9DoSFp3tv4WOJhSKOAzf8qNyalXYeXHwqSGAAUALm0"
}
```

{collapsible="true" collapsed-title="Request.rest"}
'###' denotes line separation