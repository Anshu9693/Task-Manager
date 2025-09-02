# Task Manager API

A simple Node.js, Express, and MongoDB-based Task Manager with JWT authentication. This project provides RESTful APIs for user registration, login, and CRUD operations on tasks. The frontend is built with React.

---

## Table of Contents
- [Features](#features)
- [Getting Started](#getting-started)
- [API Endpoints](#api-endpoints)
  - [User Routes](#user-routes)
  - [Task Routes](#task-routes)
- [Environment Variables](#environment-variables)
- [Deployment](#deployment)

---

## Features
- User registration and login with JWT authentication
- Create, read, update, and delete tasks
- Secure password hashing with bcrypt
- RESTful API structure
- React frontend for user interaction

---

## Getting Started

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Anshu9693/task_manager.git
   cd task_manager
   ```
2. **Install dependencies:**
   ```bash
   cd server
   npm install
   cd ../client
   npm install
   ```
3. **Set up environment variables:**
   - In `server/.env`, set:
     ```env
     DB_URL=your_mongodb_connection_string
     JWT_SECRET=your_jwt_secret
     PORT=8080
     ```
   - In `client/.env`, set:
     ```env
     REACT_APP_BACKEND_PORT=http://localhost:8080
     ```
4. **Run the backend:**
   ```bash
   cd server
   npm start
   ```
5. **Run the frontend:**
   ```bash
   cd client
   npm start
   ```

---

## API Endpoints

### User Routes

| Method | Endpoint           | Description           |
|--------|--------------------|----------------------|
| POST   | `/user/register`   | Register a new user  |
| POST   | `/user/login`      | Login a user         |

#### Register User
- **POST** `/user/register`
- **Body:**
  ```json
  {
    "fname": "FirstName",
    "lname": "LastName",
    "email": "user@example.com",
    "password": "yourpassword"
  }
  ```
- **Response:**
  ```json
  {
    "token": "<jwt_token>",
    "user": { ...userData }
  }
  ```

#### Login User
- **POST** `/user/login`
- **Body:**
  ```json
  {
    "email": "user@example.com",
    "password": "yourpassword"
  }
  ```
- **Response:**
  ```json
  {
    "token": "<jwt_token>",
    "user": { ...userData }
  }
  ```

---

### Task Routes

| Method | Endpoint         | Description         |
|--------|------------------|--------------------|
| POST   | `/task/create`   | Create a new task  |
| GET    | `/task/fetch`    | Get all tasks      |
| PUT    | `/task/:id`      | Update a task      |
| DELETE | `/task/:id`      | Delete a task      |

#### Create Task
- **POST** `/task/create`
- **Body:**
  ```json
  {
    "taskName": "My Task",
    "isDone": false
  }
  ```
- **Response:**
  ```json
  {
    "message": "Task is created",
    "success": true
  }
  ```

#### Fetch All Tasks
- **GET** `/task/fetch`
- **Response:**
  ```json
  {
    "message": "All task",
    "success": true,
    "data": [ ...tasks ]
  }
  ```

#### Update Task
- **PUT** `/task/:id`
- **Body:**
  ```json
  {
    "taskName": "Updated Task Name",
    "isDone": true
  }
  ```
- **Response:**
  ```json
  {
    "message": "Task updated",
    "success": true,
    "data": { ...updatedTask }
  }
  ```

#### Delete Task
- **DELETE** `/task/:id`
- **Response:**
  ```json
  {
    "message": "Task deleted",
    "success": true,
    "data": { ...deletedTask }
  }
  ```

---

## Environment Variables

- **Backend (`server/.env`):**
  - `DB_URL`: MongoDB connection string
  - `JWT_SECRET`: Secret for JWT token
  - `PORT`: Port for backend server (default: 8080)
- **Frontend (`client/.env`):**
  - `REACT_APP_BACKEND_PORT`: Backend API base URL

---

## Deployment

- Deploy both `client` and `server` folders as separate projects on Vercel.
- Set environment variables in the Vercel dashboard for each project.
- Update the frontend `.env` to use the deployed backend URL in production.

---

## License


