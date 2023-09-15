# My Flask API Documentation File

This documentation outlines the usage, formats, and setup instructions for the My Flask API.

## Diagram

:star:[Link](https://imgur.com/a/ggkK1TT) :star:

## Standard Request and Response Formats

### Create User (POST /api/)

**Request Format:**

```json
{
  "name": "John Doe"
}
```

Response Format (Success - HTTP 201):

```json
{
  "id": 9,
  "message": "User created successfully",
  "name": "Janet Jackson"
}
```

Response Format (Error - HTTP 400 - Validation Error):

```json
{
  "error": "Please provide a name"
}
```

Response Format (Error - HTTP 400 - Validation Error):

```json
{
  "error": "Name must be a string"
}
```

### Get User by ID (GET /api/int:user_id)

Response Format (Success - HTTP 200):

```json
{
  "id": 1,
  "name": "Harry Potter"
}
```

Response Format (Error - HTTP 404 - User Not Found):

```json
{
  "error": "User not found/id not in Database"
}
```

### Update User by ID (PUT /api/int:user_id or PATCH /api/int:user_id)

Request Format:

```json
{
  "name": "New Name"
}
```

Response Format (Success - HTTP 200):

```json
{
  "id": 15,
  "message": "User updated successfully",
  "name": "New Name"
}
```

Response Format (Error - HTTP 404 - User Not Found):

```json
{
  "error": "User not found/id not in Database"
}
```

### Delete User by ID (DELETE /api/int:user_id)

Response Format (Success - HTTP 200):

```json
{
  "id": 30,
  "message": "User deleted successfully",
  "name": "Miykael"
}
```

Response Format (Error - HTTP 404 - User Not Found):

```json
{
  "error": "User not found/id not in Database"
}
```

### List All Users (GET /api/users)

Response Format (Success - HTTP 200):

```json
[
  {
    "id": 1,
    "name": "Emmanuel Arinze"
  },
  {
    "id": 2,
    "name": "Arinze Emmanuel"
  }
]
```

## Sample Usage

### Creating a User

`Request:`

```http
POST /api/
Content-Type: application/json

{
  "name": "Jane"
}
```

`Response (HTTP 201):`

```json
{
  "id": 9,
  "message": "User created successfully",
  "name": "Donald Fin"
}
```

### Getting User by ID

`Request:`

```http
GET /api/1
```

`Response (HTTP 200):`

```json
{
  "id": 1,
  "name": "Holiday"
}
```

### Updating User by ID

`Request:`

```http
PUT /api/1
Content-Type: application/json
```

```http
{
  "name": "Updated Name"
}
```

Response (HTTP 200):

```json
{
  "id": 15,
  "message": "User updated successfully",
  "name": "Updated Name"
}
```

## Known Limitations and Assumptions

The API assumes that the name field is a required attribute for creating and updating users. It validates that the name is a string.

## Setup and Deployment Instructions

### Local Setup

1. Clone the repository:

```
git clone https://github.com/kalwhyte/hngx-SecondStage
```

Navigate to to hng-task-two directory

```
cd hngx-SecondStage
```

2. **Create a virtual environment (optional but recommended):**

```
python -m venv venv
```

```
. stage-two/bin/activate
```

3. **Install dependencies:**

```
pip install -r requirements.txt
```

5. **Run the application:**

```
python3 app.py
```

## API Endpoints
  *  GET /
  *  POST /api/: Create a new user.
  *  GET /api/<int:user_id>: Get user details by ID.
  *  PUT /api/<int:user_id>: Update user details by ID.
  *  PATCH /api/<int:user_id>: Partially update user details by ID.
  *  DELETE /api/<int:user_id>: Delete a user by ID.
  *  GET /api/users: List all users.

## Testing
To test your Flask application, you can use a tool like curl or Postman to send HTTP requests to your API and verify the responses. Here, I'll provide an example of how to use curl to test your API endpoints:

[`python3 app.py`](python3 app.py)

This starts your Flask development server, and it should be listening on `http://127.0.0.1:80`.

Open another terminal window, and you can use curl to send HTTP requests to your API. Here are some example requests for each of your API endpoints:

**Create a new user:**

    curl -X POST -H "Content-Type: application/json" -d '{"name": "John Doe"}' http://127.0.0.1:80/api/

Read a user by their ID (replace <user_id> with an actual user ID. [example: 1.]):


    curl `http://127.0.0.1:80/api/`<user_id> or [](https://hngx-second-stage.onrender.com/api/users)

Update a user's name by their ID (replace <user_id> with an actual user ID and change "New Name" to the desired name):
    curl `-X PUT -H` "Content-Type: application/json" -d '{"name": "`New Name`"}' `http://127.0.0.1:80/api/`<user_id>

Delete a user by their ID (replace <user_id> with an actual user ID):
    curl `-X DELETE http://127.0.0.1:80/api/`<user_id>


List all users:
    curl `http://127.0.0.1:80/api/users` or [](https://hngx-second-stage.onrender.com/api/users)

Access the root URL:
    curl `http://127.0.0.1:80/`

After sending each curl request, you should receive responses from your Flask application.

For example, for the "Create a new user" request, you should see a response similar to:

- `{"id": 1, "name": "John Doe", "message": "User created successfully"}`
