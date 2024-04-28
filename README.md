Task Manager API
================

Welcome to the Task Manager API! This API, built using Node.js and Express, offers a comprehensive suite of features for managing tasks and users efficiently.

Features
--------

*   **Data Validation and Sanitization**: Ensure data integrity and security with robust validation and sanitization techniques.
    
*   **Asynchronous Programming**: Utilize asynchronous programming to handle multiple tasks concurrently, ensuring optimal performance.
    
*   **CRUD Operations**: Allow users to perform Create, Read, Update, and Delete operations seamlessly on their profile and tasks.
    
*   **Multiple User Support**: Multi-user app with separate profile and tasks for each user.
    
*   **JWT Authentication**: Secure endpoints with JSON Web Tokens (JWT) for reliable user authentication.

*   **Authorization**: Limit user access to their own profile and tasks.
    
*   **Password Hashing**: Prioritize security by hashing passwords before storing them in the database.
    
*   **Login / Logout Functionality**: Enable users to log in and out securely.
  
*   **Login from Multiple Devices**: Enable users to simultaneously login from multiple devices, generating unique token for each device.
    
*   **User / Task Association**: Establish relationships between users and tasks for organized task management.
    
*   **Sorting, Pagination, and Filtering**: Easily sort, paginate, and filter tasks for efficient data retrieval.
    
*   **File Uploads**: Allow users to upload profile pictures with built-in validation for file types and sizes.

## Deployed Endpoints

### User Endpoints

#### POST /users

Register a new user:
- **Request**:
```bash
curl --location 'https://siddiqui-task-manager.vercel.app/users' \
--header 'Content-Type: application/json' \
--data-raw '{
    "name":"Example User",
    "email":"user@example.com",
    "password":"example123"
}'
```
- **Response**:
```json
{
    "user": {
        "name": "Example User",
        "email": "user@example.com",
        "_id": "662e9024d3cf469c417e7b58",
        "createdAt": "2024-04-28T18:06:28.787Z",
        "updatedAt": "2024-04-28T18:06:29.027Z",
        "__v": 1
    },
    "token": "encodedHeader.encodedPayload.encodedSignature"
}
```

#### POST /users/login

Login user:
- **Request**:
```bash
curl --location 'https://siddiqui-task-manager.vercel.app/users/login' \
--header 'Content-Type: application/json' \
--data-raw '{
    "email":"user@example.com",
    "password":"example123"
}'
```
- **Response**:
```json
{
    "user": {
        "name": "Example User",
        "email": "user@example.com",
        "_id": "662e9024d3cf469c417e7b58",
        "createdAt": "2024-04-28T18:06:28.787Z",
        "updatedAt": "2024-04-28T18:06:29.027Z",
        "__v": 1
    },
    "token": "encodedHeader.encodedPayload.encodedSignature"
}
```

#### GET /users/me

Get profile:
- **Request**:
```bash
curl --location 'https://siddiqui-task-manager.vercel.app/users/me' \
--header 'Authorization: Bearer encodedHeader.encodedPayload.encodedSignature'
```
- **Response**:
```json
{
    "_id": "662e9024d3cf469c417e7b58",
    "name": "Example User",
    "email": "user@example.com",
    "createdAt": "2024-04-28T18:06:28.787Z",
    "updatedAt": "2024-04-28T18:18:03.827Z",
    "__v": 2
}
```

#### PATCH /users/me

Update profile:
- **Request**:
```bash
curl --location --request PATCH 'https://siddiqui-task-manager.vercel.app/users/me' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer encodedHeader.encodedPayload.encodedSignature'
--data '{
    "password":"abcdefghi"
}'
```
- **Response**:
```json
{
    "_id": "662e9024d3cf469c417e7b58",
    "name": "Example User",
    "email": "user@example.com",
    "createdAt": "2024-04-28T18:06:28.787Z",
    "updatedAt": "2024-04-28T18:25:16.198Z",
    "__v": 2
}
```

#### DELETE /users/me

Delete account:
- **Request**:
```bash
curl --location --request DELETE 'https://siddiqui-task-manager.vercel.app/users/me' \
--header 'Authorization: Bearer encodedHeader.encodedPayload.encodedSignature'
```
- **Response**:
```json
{
    "_id": "662e9024d3cf469c417e7b58",
    "name": "Example User",
    "email": "user@example.com",
    "createdAt": "2024-04-28T18:06:28.787Z",
    "updatedAt": "2024-04-28T19:12:45.455Z",
    "__v": 4
}
```

#### POST /users/logout

Logout from current device:
- **Request**:
```bash
curl --location --request POST 'https://siddiqui-task-manager.vercel.app/users/logout' \
--header 'Authorization: Bearer encodedHeader.encodedPayload.encodedSignature'
```

#### POST /users/logoutAll

Logout from all devices:
- **Request**:
```bash
curl --location --request POST 'https://siddiqui-task-manager.vercel.app/users/logoutAll' \
--header 'Authorization: Bearer encodedHeader.encodedPayload.encodedSignature'
```

#### POST /users/me/avatar

Upload profile picture:
- **Request**:
```bash
curl --location 'https://siddiqui-task-manager.vercel.app/users/me/avatar' \
--header 'Authorization: Bearer encodedHeader.encodedPayload.encodedSignature'
--form 'avatar=@"/C:/Path-to-your-file/profile-image-png.png"'
```

#### DELETE /users/me/avatar

Delete profile picture:
- **Request**:
```bash
curl --location 'https://siddiqui-task-manager.vercel.app/users/me/avatar' \
--header 'Authorization: Bearer encodedHeader.encodedPayload.encodedSignature'
```


### Task Endpoints

#### POST /tasks

Create a new task:
- **Request**:
```bash
curl --location 'https://siddiqui-task-manager.vercel.app/tasks' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer encodedHeader.encodedPayload.encodedSignature'
--data '{
    "description":"example",
    "completed": "false"
}'
```
- **Response**:
```json
{
    "description": "example",
    "completed": false,
    "owner": "662e9024d3cf469c417e7b58",
    "_id": "662e99412f3acd8b53db4799",
    "createdAt": "2024-04-28T18:45:21.430Z",
    "updatedAt": "2024-04-28T18:45:21.430Z",
    "__v": 0
}
```

#### GET /tasks

Get your tasks:
- **Request**:
```bash
#### POST /tasks

Create a new task:
- **Request**:
```bash
curl --location 'https://siddiqui-task-manager.vercel.app/tasks?limit=10&skip=0&sort=createdAt-desc' \
--header 'Authorization: Bearer encodedHeader.encodedPayload.encodedSignature'

```
- **Response**:
```json
[
    {
        "_id": "662e9a392f3acd8b53db47a3",
        "description": "another example",
        "completed": true,
        "owner": "662e9024d3cf469c417e7b58",
        "createdAt": "2024-04-28T18:49:29.296Z",
        "updatedAt": "2024-04-28T18:49:29.296Z",
        "__v": 0
    },
    {
        "_id": "662e99412f3acd8b53db4799",
        "description": "example",
        "completed": false,
        "owner": "662e9024d3cf469c417e7b58",
        "createdAt": "2024-04-28T18:45:21.430Z",
        "updatedAt": "2024-04-28T18:45:21.430Z",
        "__v": 0
    }
]
```

#### PATCH /tasks/{id}

Update a task:
- **Request**:
```bash
curl --location --request PATCH 'https://siddiqui-task-manager.vercel.app/tasks/662e99412f3acd8b53db4799' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer encodedHeader.encodedPayload.encodedSignature'
--data '{
    "completed":true
}'
```
- **Response**:
```json
{
    "_id": "662e99412f3acd8b53db4799",
    "description": "example",
    "completed": true,
    "owner": "662e9024d3cf469c417e7b58",
    "createdAt": "2024-04-28T18:45:21.430Z",
    "updatedAt": "2024-04-28T18:54:32.906Z",
    "__v": 0
}
```

#### DELETE /tasks/{id}

Delete a task:
- **Request**:
```bash
curl --location --request DELETE 'https://siddiqui-task-manager.vercel.app/tasks/662e9a392f3acd8b53db47a3' \
--header 'Authorization: Bearer encodedHeader.encodedPayload.encodedSignature'
```
- **Response**:
```json
{
    "_id": "662e9a392f3acd8b53db47a3",
    "description": "another example",
    "completed": false,
    "owner": "662e9024d3cf469c417e7b58",
    "createdAt": "2024-04-28T18:49:29.296Z",
    "updatedAt": "2024-04-28T18:53:29.286Z",
    "__v": 0
}
```
