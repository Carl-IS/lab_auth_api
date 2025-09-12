# Lab Auth API

A simple authentication REST API built with Node.js, Express, and MySQL.

## Project Overview

This project provides user authentication features including signup, login, logout (token revocation), and profile retrieval. JWT is used for stateless authentication, and tokens can be revoked for logout functionality.

## Setup

1. **Clone the repository**

   git clone (https://github.com/Carl-IS/lab_auth_api.git)
   cd lab-auth-api


2. **Install dependencies**

   npm install


3. **Configure environment variables**

   Edit the `.env` file in the root directory:

   DB_HOST=localhost
   DB_USER=root
   DB_PASS=
   DB_NAME=lab_auth
   DB_PORT=3306
   SERVER_PORT=3000

   JWT_SECRET=replace_with_a_long_random_string
   JWT_EXPIRES=1h


4. **Set up the MySQL database**

    Create the database and tables:
sql
    CREATE DATABASE lab_auth;
    USE lab_auth;

    CREATE TABLE IF NOT EXISTS users (
        id INT AUTO_INCREMENT PRIMARY KEY,
        email VARCHAR(100) NOT NULL UNIQUE,
        password_hash VARCHAR(255) NOT NULL,
        full_name VARCHAR(120),
        role VARCHAR(30) DEFAULT 'student',
        created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

    CREATE TABLE IF NOT EXISTS revoked_tokens (
        id INT AUTO_INCREMENT PRIMARY KEY,
        jti VARCHAR(64) NOT NULL UNIQUE,
        expires_at DATETIME NOT NULL,
        revoked_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;


## How to Run

Start the server:

npm start

Or for development with auto-reload:

npm run dev

The API will be available at [http://localhost:3000](http://localhost:3000) (or your configured port).

## Endpoints List

| Method | Endpoint             | Description                       |
|--------|----------------------|-----------------------------------|
| GET    | `/api/health`        | Health check                      |
| POST   | `/api/auth/signup`   | Register a new user               |
| POST   | `/api/auth/login`    | Login and receive JWT token       |
| POST   | `/api/auth/logout`   | Logout (revoke JWT token)         |
| GET    | `/api/profile`       | Get authenticated user profile    |

All `/api/profile` and `/api/auth/logout` endpoints require a valid JWT token in the `Authorization: Bearer <token>` header.

## License

ISC