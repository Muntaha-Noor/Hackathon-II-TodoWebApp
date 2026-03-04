# Todo Full-Stack Web Application

A full-stack todo application with user authentication, AI chatbot assistant, and task management capabilities built with Next.js, FastAPI, and PostgreSQL.

---

## Features

- User authentication with Better Auth (JWT)  
- Task CRUD operations (Create, Read, Update, Delete)  
- Task completion toggling  
- User-specific task filtering  
- AI Chatbot - Natural language task management via MCP tools  
- Responsive UI with Tailwind CSS  
- Docker Support - Containerized deployment  

---

## Tech Stack

- **Frontend:** Next.js 16+, TypeScript, Tailwind CSS  
- **Backend:** FastAPI, SQLModel, MCP Tools  
- **Database:** SQLite (dev) / Neon Serverless PostgreSQL (prod)  
- **Authentication:** Better Auth (JWT)  
- **AI:** OpenAI Agents SDK compatible  

---

## Prerequisites

### For Local Development

- Node.js 18+  
- Python 3.9+  

### For Docker Deployment

- Docker Desktop (Windows/Mac) or Docker Engine (Linux)  
- Docker Compose  

---

## Quick Start with Docker

```bash
# Build images
./build-docker.sh        # Linux/macOS
.\build-docker.ps1       # Windows PowerShell

# Run application
docker compose up

# Access at http://localhost:3000
