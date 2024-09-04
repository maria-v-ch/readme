# FastAPI Users API Documentation

## Overview

This FastAPI application provides a basic RESTful API to manage users. The API allows clients to perform CRUD 
(Create, Read, Update, Delete) operations on a list of users. Each user has an id, username, wallet, and birthdate.

## Endpoints

### 1. Get All Users
* URL: `/users/`
* Method: `GET`
* Description: Retrieve a list of all users in the database.
* Response: A list of `User` objects.

**Example HTTP Request:**

    GET /users/

**Example JSON Response:**

    [
        {
            "id": 1,
            "username": "user1",
            "wallet": 100.0,
            "birthdate": "1990-01-01"
        },
        {
            "id": 2,
            "username": "user2",
            "wallet": 200.0,
            "birthdate": "1995-05-15"
        }
    ]

### 2. Get User by ID
* URL: `/users/{user_id}`
* Method: `GET`
* Description: Retrieve a specific user by their unique ID.
* Path Parameter:
  * `user_id` (int): The ID of the user to retrieve.
* Response: A `User` object if the user is found.
* Error Response: `404 Not Found` if the user with the given ID does not exist.

**Example HTTP Request:**
    
    GET /users/1

**Example JSON Response:**

    {
        "id": 1,
        "username": "user1",
        "wallet": 100.0,
        "birthdate": "1990-01-01"
    }

### 3. Create a New User
* URL: `/users/`
* Method: `POST`
* Description: Create a new user and add them to the database.
* Request Body: A `User` object containing the user's data.
* Response: The newly created `User` object.

**Example HTTP Request:**
    
    POST /users/
    Content-Type: application/json

    {
        "id": 3,
        "username": "user3",
        "wallet": 300.0,
        "birthdate": "2000-12-25"
    }


**Example JSON Response:**

    {
        "id": 3,
        "username": "user3",
        "wallet": 300.0,
        "birthdate": "2000-12-25"
    }

### 4. Update an Existing User
* URL: `/users/{user_id}`
* Method: `PUT`
* Description: Update an existing user's data by their ID.
* Path Parameter:
  * `user_id` (int): The ID of the user to update.
* Request Body: A `User` object containing the updated data.
* Response: The updated `User` object.
* Error Response: `404 Not Found` if the user with the given ID does not exist.

**Example HTTP Request:**
    
    PUT /users/1
    Content-Type: application/json
    
    {
        "id": 1,
        "username": "updated_user1",
        "wallet": 150.0,
        "birthdate": "1990-01-01"
    }


**Example JSON Response:**

    {
        "id": 1,
        "username": "updated_user1",
        "wallet": 150.0,
        "birthdate": "1990-01-01"
    }

### 5. Delete a User
* URL: `/users/{user_id}`
* Method: `DELETE`
* Description: Delete a user from the database by their ID.
* Path Parameter:
  * `user_id` (int): The ID of the user to delete.
* Response: The deleted `User` object.
* Error Response: `404 Not Found` if the user with the given ID does not exist.

**Example HTTP Request:**
    
    DELETE /users/1

**Example JSON Response:**

    {
        "id": 1,
        "username": "user1",
        "wallet": 100.0,
        "birthdate": "1990-01-01"
    }

## Models
### User Model
* id (int): The unique identifier of the user.
* username (str): The username of the user.
* wallet (float): The amount of money in the user's wallet.
* birthdate (date): The birthdate of the user.

Example JSON representation:

    {
        "id": 1,
        "username": "user1",
        "wallet": 100.0,
        "birthdate": "1990-01-01"
    }

## Error Handling

`404 Not Found`: This error is returned when the requested user is not found in the database. The response will 
include a JSON object with a detail field explaining the error.

Example:

    {
        "detail": "User not found"
    }

## Running the Application
To run the application, use the following command (bash):

    uvicorn app_name:app --reload

Replace app_name with the name of your Python file. The application will be accessible at http://127.0.0.1:8000. 

## Conclusion
This FastAPI application provides a simple yet functional API for managing users. It allows clients to create, read, 
update, and delete user data in a straightforward manner.
