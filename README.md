Todo Full-Stack Web Application
A full-stack todo application with user authentication, AI chatbot assistant, and task management capabilities built with Next.js, FastAPI, and PostgreSQL.

Features
User authentication with Better Auth (JWT)
Task CRUD operations (Create, Read, Update, Delete)
Task completion toggling
User-specific task filtering
AI Chatbot - Natural language task management via MCP tools
Responsive UI with Tailwind CSS
Docker Support - Containerized deployment
Tech Stack
Frontend: Next.js 16+, TypeScript, Tailwind CSS
Backend: FastAPI, SQLModel, MCP Tools
Database: SQLite (dev) / Neon Serverless PostgreSQL (prod)
Authentication: Better Auth (JWT)
AI: OpenAI Agents SDK compatible
Prerequisites
For Local Development:

Node.js 18+
Python 3.9+
For Docker Deployment:

Docker Desktop (Windows/Mac) or Docker Engine (Linux)
Docker Compose
Quick Start with Docker
# Build images
./build-docker.sh        # Linux/macOS
.\build-docker.ps1       # Windows PowerShell

# Run application
docker compose up

# Access at http://localhost:3000
See DOCKER.md for complete Docker deployment instructions.

Setup Instructions
Backend Setup
Navigate to the backend directory:

cd backend
Create a virtual environment and activate it:

python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
Install dependencies:

pip install -r requirements.txt
Set up environment variables:

cp .env.example .env
Then edit .env with your configuration:

DATABASE_URL=your_postgresql_connection_string
BETTER_AUTH_SECRET=your_jwt_secret
Run the backend server:

python main.py
The backend will be available at http://localhost:8000.

Frontend Setup
Navigate to the frontend directory:

cd frontend
Install dependencies:

npm install
Set up environment variables:

cp .env.example .env.local
Then edit .env.local with your configuration:

NEXT_PUBLIC_API_URL=http://localhost:8000
NEXT_PUBLIC_BETTER_AUTH_SECRET=your_jwt_secret
Run the development server:

npm run dev
The frontend will be available at http://localhost:3000.

API Endpoints
The application follows RESTful API conventions:

GET /api/{user_id}/tasks - Get all tasks for a user
POST /api/{user_id}/tasks - Create a new task
GET /api/{user_id}/tasks/{id} - Get a specific task
PUT /api/{user_id}/tasks/{id} - Update a task
PATCH /api/{user_id}/tasks/{id}/complete - Toggle task completion
DELETE /api/{user_id}/tasks/{id} - Delete a task
All endpoints require JWT authentication in the Authorization header:

Authorization: Bearer {jwt_token}
Environment Variables
Backend
DATABASE_URL - PostgreSQL connection string
BETTER_AUTH_SECRET - Secret for JWT token signing
Frontend
NEXT_PUBLIC_API_URL - Backend API URL
NEXT_PUBLIC_BETTER_AUTH_SECRET - Same secret as backend (for consistency)
Running the Application
Start the backend server first:

cd backend
python main.py
In a new terminal, start the frontend:

cd frontend
npm run dev
Open your browser to http://localhost:3000 to use the application.

Database Schema
The application uses a single tasks table with the following columns:

id - Primary key, auto-incrementing integer
user_id - String, references Better Auth user ID
title - String (1-200 characters), required
description - String (max 1000 characters), optional
completed - Boolean, default false
created_at - Timestamp with timezone
updated_at - Timestamp with timezone
Authentication Flow
Users register/login via the /auth page
Better Auth generates a JWT token
Token is stored in browser (localStorage/cookies)
Token is sent with each authenticated request
Backend verifies the token and ensures user_id matches the request
Deployment
Backend (to production)
Deploy to a cloud provider (AWS, GCP, Azure, etc.)
Set environment variables securely
Ensure database connection is configured for production
Frontend (to production)
Build the application: npm run build
Serve the static files using a web server (Vercel, Netlify, etc.)
Configure environment variables for production API URL
Project Structure
todo-app/
├── specs/                 # Specification files
│   ├── overview.md
│   ├── features/
│   ├── api/
│   ├── database/
│   └── ui/
├── frontend/              # Next.js frontend
│   ├── app/              # Next.js App Router pages
│   ├── components/       # React components
│   ├── lib/              # Utility functions
│   └── types/            # TypeScript definitions
└── backend/              # FastAPI backend
    ├── main.py           # Main application file
    ├── models.py         # Database models
    ├── database.py       # Database configuration
    ├── auth.py           # Authentication utilities
    └── routes.py         # API route definitions
License
MIT License
