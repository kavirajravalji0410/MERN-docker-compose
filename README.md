# MERN Stack Application using Docker Compose

![Docker](https://img.shields.io/badge/Docker-Compose-blue)
![Node.js](https://img.shields.io/badge/Node.js-18-green)
![MongoDB](https://img.shields.io/badge/MongoDB-8.x-brightgreen)
![React](https://img.shields.io/badge/React-Vite-blue)
![Status](https://img.shields.io/badge/Status-Working-success)

This repository contains a **MERN stack application** (MongoDB, Express, React, Node.js) running locally using **Docker Compose**.

The goal of this project is to understand:

- How multiple services work together in Docker
- Docker networking between frontend, backend, and database
- Common mistakes (like accessing MongoDB from a browser)
- Real-world local development setup using containers

This is a **learning and practice project**, not a production deployment.

---

## Tech Stack

- **Frontend:** React (Vite)
- **Backend:** Node.js + Express
- **Database:** MongoDB
- **Containerization:** Docker
- **Orchestration:** Docker Compose

---

## Project Structure

```text
mern/
├── frontend/                 # React frontend (Vite)
│   ├── Dockerfile
│   └── src/
├── backend/                  # Node.js + Express API
│   ├── Dockerfile
│   └── src/
├── docker-compose.yaml       # Docker Compose configuration
└── README.md
```


## Prerequisites

Make sure you have the following installed:

- Docker Desktop
- Git

No local Node.js or MongoDB installation is required.

---

## How to Run the Application

### 1. Clone the repository

```bash
git clone https://github.com/kavirajravalji0410/MERN-docker-compose.git
cd MERN-docker-compose/mern
```

### 2. Start all services
docker compose up -d --build
Docker will build images and start:

- Frontend
- Backend
- MongoDB

### Application URLs
| Service  | URL                                            |
| -------- | ---------------------------------------------- |
| Frontend | [http://localhost:5173](http://localhost:5173) |
| Backend  | [http://localhost:5050](http://localhost:5050) |
| MongoDB  | mongodb://localhost:27017                      |

### About Backend (Cannot GET /)
If you open:
```
http://localhost:5050
```

You will see:
```
Cannot GET /
```
This is **normal**.
 - The backend is running correctly
 - No route is defined for /
 - API routes are exposed under /api/*
This confirms the backend container is healthy.

### Important Note About MongoDB (Very Common Confusion)
MongoDB is not a web server.
 - MongoDB does not use HTTP
 - Browsers use HTTP
 - MongoDB uses a binary TCP protocol
  So this will always fail:
```
  http://localhost:27017
```
Browser ❌ → MongoDB ❌

This is expected behavior. 
There is nothing to fix.

###  Correct Ways to Verify MongoDB
### Method 1: Check MongoDB logs
```
docker compose logs mongodb
```
You should see:
```
You should see:
```
This means MongoDB is ready.

### Method 2: Connect using Mongo Shell
