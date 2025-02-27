---
{"dg-publish":true,"permalink":"/api-documentation/"}
---

# API Documentation Template for Angular + Strapi Tech Stack

## **Overview**

This document provides a structured guide to consuming the API built using **Strapi** as the backend and **Angular** as the frontend. It covers authentication, CRUD operations, error handling, and response formats.

## **Base URL**

```plaintext
https://api.example.com
```

## **Authentication**

The API uses **JWT (JSON Web Token)** authentication. Users must authenticate and include the token in the `Authorization` header.

### **Login**

**Endpoint:**

```http
POST /auth/local
```

**Request Body:**

```json
{
  "identifier": "user@example.com",
  "password": "yourpassword"
}
```

**Response:**

```json
{
  "jwt": "eyJhbGciOiJIUz...",
  "user": {
    "id": 1,
    "username": "username",
    "email": "user@example.com"
  }
}
```

### **Secured API Calls**

All authenticated requests must include:

```plaintext
Authorization: Bearer <token>
```

---

## **User Management**

### **Create a User**

**Endpoint:**

```http
POST /users
```

**Request Body:**

```json
{
  "username": "JohnDoe",
  "email": "johndoe@example.com",
  "password": "SecurePass123"
}
```

**Response:**

```json
{
  "id": 2,
  "username": "JohnDoe",
  "email": "johndoe@example.com"
}
```

### **Get User Details**

**Endpoint:**

```http
GET /users/:id
```

**Response:**

```json
{
  "id": 2,
  "username": "JohnDoe",
  "email": "johndoe@example.com"
}
```

### **Update User**

**Endpoint:**

```http
PUT /users/:id
```

**Request Body:**

```json
{
  "username": "NewName"
}
```

**Response:**

```json
{
  "id": 2,
  "username": "NewName",
  "email": "johndoe@example.com"
}
```

### **Delete User**

**Endpoint:**

```http
DELETE /users/:id
```

**Response:**

```json
{
  "message": "User deleted successfully"
}
```

---

## **CRUD Operations Example (Blog Posts)**

### **Create a Post**

**Endpoint:**

```http
POST /posts
```

**Request Body:**

```json
{
  "title": "New Post",
  "content": "This is the post content.",
  "author": 1
}
```

**Response:**

```json
{
  "id": 1,
  "title": "New Post",
  "content": "This is the post content.",
  "author": {
    "id": 1,
    "username": "JohnDoe"
  }
}
```

### **Get All Posts**

**Endpoint:**

```http
GET /posts
```

**Response:**

```json
[
  {
    "id": 1,
    "title": "New Post",
    "content": "This is the post content.",
    "author": {
      "id": 1,
      "username": "JohnDoe"
    }
  }
]
```

### **Update a Post**

**Endpoint:**

```http
PUT /posts/:id
```

**Request Body:**

```json
{
  "title": "Updated Title"
}
```

**Response:**

```json
{
  "id": 1,
  "title": "Updated Title",
  "content": "This is the post content.",
  "author": {
    "id": 1,
    "username": "JohnDoe"
  }
}
```

### **Delete a Post**

**Endpoint:**

```http
DELETE /posts/:id
```

**Response:**

```json
{
  "message": "Post deleted successfully"
}
```

---

## **Error Handling**

Errors follow a consistent format:

**Example Response:**

```json
{
  "statusCode": 400,
  "error": "Bad Request",
  "message": "Invalid email or password"
}
```

### **Common Error Codes**

|Status Code|Meaning|
|---|---|
|400|Bad Request – Invalid input|
|401|Unauthorized – Invalid Token|
|403|Forbidden – Insufficient permissions|
|404|Not Found – Resource does not exist|
|500|Server Error – Unexpected issue|

---

## **Pagination & Query Parameters**

For list-based endpoints, **pagination** and **filters** can be applied.

### **Example Query:**

```http
GET /posts?_limit=10&_start=0&author=1
```

### **Query Parameters:**

|Parameter|Description|
|---|---|
|`_limit`|Number of results per page|
|`_start`|Offset for pagination|
|`author`|Filter by author ID|

---