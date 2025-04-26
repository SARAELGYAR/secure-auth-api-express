

# Express Authentication & RBAC System

A secure Express.js API implementation featuring JWT authentication, password hashing, and role-based access control (`user`, `moderator`, `admin`).

---

## ✨ Features

- User Registration and Login
- Password Hashing with bcrypt
- JWT-Based Authentication
- Role-Based Access Control (RBAC)
- Public and Protected Routes
- Basic User Management (Profile and Role Updates)
- Security Enhancements:
  - Rate Limiting
  - Secure Password Storage
  - JWT Token Expiration
  - Secure Error Handling

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v14 or higher)
- [npm](https://www.npmjs.com/) (v6 or higher)

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Environment Variables**

   Create a `.env` file in the root directory and add:

   ```plaintext
   PORT=3000
   JWT_SECRET=your_super_secure_jwt_secret_key_change_in_production
   JWT_EXPIRES_IN=3600
   ```

4. **Run the server**
   ```bash
   npm start
   ```

---

## 📋 API Endpoints

### Authentication

- **POST** `/api/register` — Register a new user  
  **Body**:
  ```json
  {
    "username": "user1",
    "email": "user@example.com",
    "password": "Password1!",
    "role": "user"
  }
  ```

- **POST** `/api/login` — Login with username and password  
  **Body**:
  ```json
  {
    "username": "user1",
    "password": "Password1!"
  }
  ```

---

### Public Routes

- **GET** `/api/public` — Public route accessible by everyone

---

### Protected Routes (Require Authentication)

- **GET** `/api/protected` — Protected route for any authenticated user
- **GET** `/api/moderator` — Route for `moderator` or `admin`
- **GET** `/api/admin` — Route for `admin` only

---

### User Profile Management

- **GET** `/api/profile` — Get authenticated user's profile
- **PUT** `/api/profile` — Update email and/or password  
  **Body**:
  ```json
  {
    "email": "new.email@example.com",
    "password": "NewPassword1!"
  }
  ```

---

### User Management (Admin Only)

- **PUT** `/api/users/:id/role` — Update user role  
  **Body**:
  ```json
  {
    "role": "moderator"
  }
  ```

---

## 🔒 Security Features

- Passwords are hashed using bcrypt before storage
- JWT tokens have expiration time (`1 hour`)
- Role-based access control for route protection
- Rate limiting on sensitive routes (`/api/register`, `/api/login`)
- Secure error handling to avoid leaking server internals
- Input validation for email format and strong password enforcement

---

## 🧪 Testing the API

You can test using **Postman** or **cURL**.

### Example cURL Commands

- **Register a New User**
  ```bash
  curl -X POST http://localhost:3000/api/register \
    -H "Content-Type: application/json" \
    -d '{"username":"admin1","email":"admin@example.com","password":"Password1!","role":"admin"}'
  ```

- **Login**
  ```bash
  curl -X POST http://localhost:3000/api/login \
    -H "Content-Type: application/json" \
    -d '{"username":"admin1","password":"Password1!"}'
  ```

- **Access Protected Route**
  ```bash
  curl -X GET http://localhost:3000/api/protected \
    -H "Authorization: Bearer YOUR_TOKEN_HERE"
  ```

- **Update User Role (Admin Only)**
  ```bash
  curl -X PUT http://localhost:3000/api/users/USER_ID/role \
    -H "Authorization: Bearer YOUR_ADMIN_TOKEN" \
    -H "Content-Type: application/json" \
    -d '{"role":"moderator"}'
  ```

---

## 📂 Project Structure

```
/controllers
  authController.js
  userController.js
/middlewares
  authMiddleware.js
  roleMiddleware.js
/routes
  authRoutes.js
  userRoutes.js
.env
server.js
package.json
README.md
```

---


