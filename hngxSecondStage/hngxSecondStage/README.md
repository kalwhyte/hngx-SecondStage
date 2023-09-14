# My Flask API Documentation

This documentation outlines the usage, formats, and setup instructions for the My Flask API.

## UML Diagram

https://imgur.com/a/d1ECDQm
![UML DIAGRAM](UML-Diagram.png)

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
  "name": "John Doe"
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
  "name": "John Doe"
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
  "name": "Temitope"
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
    "name": "John Doe"
  },
  {
    "id": 2,
    "name": "Jane Smith"
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
  "name": "Alice"
}
```

`Response (HTTP 201):`

```json
{
  "id": 9,
  "message": "User created successfully",
  "name": "John Doe"
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
  "name": "Alice"
}
```

### Updating User by ID

`Request:`

````http
PUT /api/1
Content-Type: application/json
```http
{
  "name": "Updated Name"
}
````

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

```h
git clone https://github.com/kalwhyte/hngxSecondStage
```

Navigate to to hng-task-two directory

```sh
cd hng-task-two
```

2. **Create a virtual environment (optional but recommended):**

```sh
python -m venv venv
```

```sh
source venv/bin/activate  # On Windows, use venv\Scripts\activate
```

3. **Install dependencies:**

```sh
pip install -r requirements.txt
```

4. **Create a .env file in the project root directory with the following content:**

```sh
DATABASE_URI=mysql+pymysql://username:password@localhost/mydatabase
```

5. **Run the application:**

```
python3 app.py
```

## API Endpoints

  *  POST /api/: Create a new user.
  *  GET /api/<int:user_id>: Get user details by ID.
  *  PUT /api/<int:user_id>: Update user details by ID.
  *  PATCH /api/<int:user_id>: Partially update user details by ID.
  *  DELETE /api/<int:user_id>: Delete a user by ID.
  *  GET /api/users: List all users.

## Testing
To test your Flask application, you can use a tool like curl or Postman to send HTTP requests to your API and verify the responses. Here, I'll provide an example of how to use curl to test your API endpoints:

[`python3 app.py`](python3 app.py)

This starts your Flask development server, and it should be listening on `http://127.0.0.1:5000`.

Open another terminal window, and you can use curl to send HTTP requests to your API. Here are some example requests for each of your API endpoints:

**Create a new user:**

curl -X POST -H "Content-Type: application/json" -d '{"name": "John Doe"}' http://127.0.0.1:5000/api/

Read a user by their ID (replace <user_id> with an actual user ID. [example: 1.]):


curl `http://127.0.0.1:5000/api/`<user_id>
Update a user's name by their ID (replace <user_id> with an actual user ID and change "New Name" to the desired name):

curl `-X PUT -H` "Content-Type: application/json" -d '{"name": "`New Name`"}' `http://127.0.0.1:5000/api/`<user_id>
Delete a user by their ID (replace <user_id> with an actual user ID):


curl `-X DELETE http://127.0.0.1:5000/api/`<user_id>
List all users:


curl `http://127.0.0.1:5000/api/users`
Access the root URL:


curl `http://127.0.0.1:5000/`

After sending each curl request, you should receive responses from your Flask application.

For example, for the "Create a new user" request, you should see a response similar to:

- `{"id": 1, "name": "John Doe", "message": "User created successfully"}`
