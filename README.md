# Local Development Setup Guide

## Prerequisites

Before you begin, ensure you have the following installed:
- Python 3.10 or higher
- Poetry 
- MongoDB 6.0
- Git
- Docker 


### 1. Clone the Repository
```bash
git clone <repository-url>
cd flask-crud
```

### 2. Environment Setup
Create a `.env` file in the root directory with the following variables:
```plaintext
FLASK_APP=app.main.py:create_app()
FLASK_ENV=development
MONGODB_URI=mongodb://localhost:27017/
MONGODB_DB=user_management
JWT_SECRET_KEY=your-secret-key
```

### 3. Install Dependencies
```bash
poetry install
```

### 4. Start MongoDB
Ensure MongoDB is running locally on port 27017. If you need to start it manually:
```bash
mongod --dbpath /path/to/your/data/directory
```

### 5. Run the Application
```bash
poetry run flask run
```

The API will be available at `http://localhost:5000`

## Docker Setup

### 1. Clone the Repository
```bash
git clone <repository-url>
cd flask-crud
```

### 2. Environment Setup
Create a `.env` file with just the JWT secret(You can generate your JWT key through secrets or random):
```plaintext
JWT_SECRET_KEY=your-secret-key-here
```

### 3. Build and Run with Docker Compose
```bash
docker compose up --build
```

The API will be available at `http://localhost:5000`

## Verify Installation

Once running, you can access:
- API Documentation: `http://localhost:5000/swagger-ui`
- API Base URL: `http://localhost:5000/api/v1`

## API Endpoints

The following endpoints are available:
- `POST /api/v1/users` - Create a new user
- `GET /api/v1/users` - List all users (requires authentication)
- `GET /api/v1/users/<id>` - Get a specific user (requires authentication)
- `PUT /api/v1/users/<id>` - Update a user (requires authentication)
- `DELETE /api/v1/users/<id>` - Delete a user (requires authentication)
- `POST /api/v1/login` - Login and get JWT token

Note: All authenticated endpoints require a valid JWT token in the Authorization header: `Bearer <token>`
