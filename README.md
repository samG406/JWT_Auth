# Node.js Express REST API with JWT Authentication
This project is a demonstration of building a Node.js REST API using Express, MySQL, and Sequelize, implementing token-based authentication using JWT (JSON Web Token). It provides secure authentication and role-based authorization for users.

# Features
-- User registration & login with JWT authentication
-- Role-based access control (user, moderator, admin)
-- Sequelize ORM integration with MySQL
-- Organized structure using MVC and middleware pattern
-- CORS configuration
-- RESTful API tested with Postman

# Project Structure
.
├── config/
│   ├── db.config.js         # MySQL DB & Sequelize configuration
│   └── auth.config.js       # JWT secret key
├── controllers/
│   ├── auth.controller.js   # Signup & Signin logic
│   └── user.controller.js   # Access to public & protected content
├── middlewares/
│   ├── authJwt.js           # Verify JWT token & roles
│   └── verifySignUp.js      # Check for duplicate usernames/emails
├── models/
│   ├── index.js             # Sequelize init & associations
│   ├── role.model.js        # Role model
│   └── user.model.js        # User model
├── routes/
│   ├── auth.routes.js       # Signup & Signin endpoints
│   └── user.routes.js       # Public & protected routes
├── server.js                # Entry point – sets up Express app
└── README.md

 # Setup & Run
1. Clone the Repository
2. Install Dependencies
3. Configure Database
Update config/db.config.js with your MySQL settings:
module.exports = {
  HOST: "localhost",
  USER: "your-db-user",
  PASSWORD: "your-db-password",
  DB: "your-database-name",
  dialect: "mysql",
  pool: {
    max: 5,
    min: 0,
    acquire: 30000,
    idle: 10000
  }
};
4. Run the Server
node server.js
Server will be running on http://localhost:8080/

# API Endpoints
Auth Routes (auth.routes.js)
POST /api/auth/signup — Register a new user
POST /api/auth/signin — Login and get JWT token
User Routes (user.routes.js)
GET /api/test/all — Public content
GET /api/test/user — Protected (requires user role)
GET /api/test/mod — Protected (requires moderator role)
GET /api/test/admin — Protected (requires admin role)

# Key Learnings
 **Designing a secure JWT auth flow (signup/login)**
 **Structuring Express apps with middlewares and MVC**
 **Managing roles and access control in Sequelize**
 **Using Sequelize associations to link users with roles**
 **Integrating and testing APIs using Postman**

# Technologies Used

*Node.js*
*Express*
*MySQL*
*Sequelize*
*JWT (jsonwebtoken)*
*bcryptjs*
*CORS*
