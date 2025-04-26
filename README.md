Express Authentication & RBAC System
A secure Express.js API implementation with JWT authentication and role-based access control.

Features
User registration and login
Password hashing using bcrypt
JWT-based authentication
Role-based access control (user, moderator, admin)
Protected and public routes
Basic user management features
Security enhancements (rate limiting, secure password storage)
Getting Started
Prerequisites
Node.js (v14 or higher)
npm (v6 or higher)
Installation
Clone the repository:

git clone <repository-url>
Install dependencies:

npm install
Create a .env file in the root directory with the following variables:

PORT=3000
JWT_SECRET=your_super_secure_jwt_secret_key_change_in_production
JWT_EXPIRES_IN=3600
Start the server:

npm start
API Endpoints
Authentication
POST /api/register - Register a new user

Body: { "username": "user1", "email": "user@example.com", "password": "Password1!", "role": "user" }
POST /api/login - Login with username and password

Body: { "username": "user1", "password": "Password1!" }
Public Routes
GET /api/public - Public route accessible by everyone
Protected Routes
GET /api/protected - Protected route (requires authentication)
GET /api/moderator - Moderator route (requires moderator or admin role)
GET /api/admin - Admin route (requires admin role)
User Profile
GET /api/profile - Get user profile (requires authentication)
PUT /api/profile - Update user profile (requires authentication)
Body: { "email": "new.email@example.com", "password": "NewPassword1!" }
User Management
PUT /api/users/:id/role - Update user role (requires admin role)
Body: { "role": "moderator" }
Security Features
Password hashing using bcrypt
JWT token with expiration
Role-based access control
Rate limiting for login and registration
Secure error handling
Email and password validation
Testing the API
You can test the API using tools like Postman or cURL.

Example cURL Commands
Register a new user:

curl -X POST http://localhost:3000/api/register -H "Content-Type: application/json" -d '{"username":"admin1","email":"admin@example.com","password":"Password1!","role":"admin"}'
Login:

curl -X POST http://localhost:3000/api/login -H "Content-Type: application/json" -d '{"username":"admin1","password":"Password1!"}'
Access protected route (replace TOKEN with your JWT token):

curl -X GET http://localhost:3000/api/protected -H "Authorization: Bearer TOKEN"
Update user role (replace TOKEN with admin JWT token and USER_ID with target user ID):

curl -X PUT http://localhost:3000/api/users/USER_ID/role -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"role":"moderator"}'
