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

*config/*
This folder contains configuration settings for the application.

•	db.config.js
Configures the connection settings for the MySQL database and sets Sequelize parameters like host, username, password, and database name.

•	auth.config.js
Stores the secret key used to sign and verify JWT tokens. Critical for ensuring secure token-based authentication.

*controllers/*
Handles the core business logic and acts as a middle layer between routes and models.

•	auth.controller.js
Manages user authentication actions such as sign-up and sign-in. Handles password encryption, user creation, and token generation.

•	user.controller.js
Controls access to different types of content depending on user roles. Returns responses for public, user, moderator, and admin endpoints.

*middlewares/*
Houses middleware functions that process requests before they reach route handlers.

•	authJwt.js
Middleware that:
o	Verifies the presence and validity of JWT tokens in requests.
o	Checks if the user has the required role to access certain resources.

•	verifySignUp.js
Middleware used during the sign-up process to:
o	Check if the provided username or email already exists in the database.
o	Prevent duplicate account creation.

*models/*
Defines Sequelize models and database associations.

•	index.js
Initializes Sequelize, imports models, and defines associations (e.g., a user can have multiple roles).

•	role.model.js
Defines the structure of the Role model, used for implementing role-based access control.

•	user.model.js
Defines the User model, including properties like username, email, password, and roles.

*routes/*
Defines application routes and maps them to corresponding controller methods.

•	auth.routes.js
Contains routes related to user authentication:
o	POST /api/auth/signup
o	POST /api/auth/signin

•	user.routes.js
Contains routes for fetching different types of content:
o	Public (GET /api/test/all)
o	Protected (user, moderator, admin)


*server.js*
The entry point of the application. It:
•	Initializes the Express app
•	Applies middleware (CORS, body-parser, etc.)
•	Sets up route handling
•	Connects to the MySQL database
•	Starts the HTTP server and listens for incoming requests


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
#*Auth Routes (auth.routes.js)*
1. POST /api/auth/signup — Register a new user
2. POST /api/auth/signin — Login and get JWT token
3. User Routes (user.routes.js)
4. GET /api/test/all — Public content
5. GET /api/test/user — Protected (requires user role)
6. GET /api/test/mod — Protected (requires moderator role)
7. GET /api/test/admin — Protected (requires admin role)

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
