# User API Spec

## Register New User
Method: POST

Endpoint: /api/register

Request body:
```json
{
    "fullname": "My Full Name",
    "username": "myUserName",
    "email": "my_email@example.com",
    "password": "myPassword"
}
```

Response body (success):
```json
{
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbG9jYWxob3N0OjgwODEvYXBpL3JlZ2lzdGVyIiwiaWF0IjoxNzU4NDMzNjcyLCJleHAiOjE3NTg0MzcyNzIsIm5iZiI6MTc1ODQzMzY3MiwianRpIjoiR3JHUlFNVlF5dWdnZ01DRyIsInN1YiI6IjgiLCJwcnYiOiIyM2JkNWM4OTQ5ZjYwMGFkYjM5ZTcwMWM0MDA4NzJkYjdhNTk3NmY3In0.osWlJXB-J4ZxWAYyDtyKKc1ILJ2jY27Oa5Sn0W5mwtc",
    "token_type": "bearer",
    "expires_in": 3600
}
```

Response code (failed):
```json
{
  "error": "Internal Server Error"
}
```

Response body (failed): 
```json
{
  "error": "Username is empty"
}
```

## Login User
Method: POST

Endpoint: /api/login

Request body:
```json
{
    "email": "my_email@example.com",
    "password": "myPassword"
}
```

Response body (success):
```json
{
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMjUyYjg0Mzc2NjY1Lm5ncm9rLWZyZWUuYXBwL2FwaS9sb2dpbiIsImlhdCI6MTc1ODQzNzM4MCwiZXhwIjoxNzU4NDQwOTgwLCJuYmYiOjE3NTg0MzczODAsImp0aSI6InpKNWxHZlBjVnNPdVBsN08iLCJzdWIiOiI5IiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.XsfJHsg79zSuEFxQ1Ke2smC3yYin_bZjbzghyOMymzI",
  "token_type": "bearer",
  "expires_in": 3600,
  "user": {
    "id": 9,
    "username": "myUserName",
    "fullname": "My Full Name",
    "email": "my_email@example.com",
    "email_verified_at": null,
    "created_at": "2025-09-21T06:49:08.000000Z",
    "updated_at": "2025-09-21T06:49:08.000000Z"
  }
}
```

Response body (failed):
```json
{
  "status": 502,
  "data": "Internal Server Error"
}
```

Response body (failed):
```json
{
  "status": 400,
  "data": "Username is empty"
}
```

## Get Profile
Method: GET 

Endpoint: /api/profile

Headers:

- Authorization : Bearer {{token}}
- Accept : application/json
- Content-Type : application/json

Response body (success):
```json
{
  "id": 8,
  "username": "myUserName",
  "fullname": "My Full Name",
  "email": "my_email@example.com",
  "email_verified_at": null,
  "created_at": "2025-09-21T05:47:52.000000Z",
  "updated_at": "2025-09-21T05:47:52.000000Z"
}
```

Response body (failed):
```json
{
  "status": 502,
  "data": "Internal Server Error"
}
```

## Logout User 
Method: POST

Endpoint: /api/logout

Headers:

- Authorization : Bearer {{token}}

Response body (failed):
```json
{
  "message": "Logout success"
}
```