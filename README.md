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

This is a **learning + practice project**, not a production deployment.

---

## Tech Stack

- **Frontend:** React (Vite)
- **Backend:** Node.js + Express
- **Database:** MongoDB
- **Containerization:** Docker
- **Orchestration:** Docker Compose

---

## Project Structure

mern/
├── frontend/ # React frontend (Vite)
│ ├── Dockerfile
│ └── src/
├── backend/ # Node.js + Express API
│ ├── Dockerfile
│ └── src/
├── docker-compose.yaml # Docker Compose configuration
└── README.md



## How to Run the Application

### 1. Clone the repository

```bash
git clone https://github.com/kavirajravalji0410/MERN-docker-compose.git
cd MERN-docker-compose/mern



2. Start all services using Docker Compose
```bash
docker compose up -d --build


Docker will build the images and start the following containers:

Frontend (React – Vite)

Backend (Node.js – Express)

MongoDB (Database)


Verify the Application

Once all containers are running, open the following URLs in your browser.

Frontend
http://localhost:5173


You should see the employee management UI with existing records.



Backend
http://localhost:5050


You will see:

Cannot GET /


This is expected behavior.
The backend is running correctly, but no route is defined for /.
API endpoints are exposed under /api/*.



MongoDB (Important Note)

Do NOT try to open MongoDB in a browser:

http://localhost:27017


MongoDB is not an HTTP service, so the browser will always fail.
This does not mean MongoDB is down.

How to Confirm MongoDB Is Running (Correct Way)
Option 1: Check MongoDB logs
docker compose logs mongodb


If you see:

Waiting for connections


MongoDB is ready.

Option 2: Connect using Mongo Shell
docker exec -it mern-mongodb-1 mongosh


If the shell opens and you see:

test>


MongoDB is running correctly.

You can verify data using:

show dbs


Docker Networking (Internal Communication)

Inside the Docker Compose network:

Frontend communicates with backend using:

http://backend:5050


Backend connects to MongoDB using:

mongodb://mongo:27017/employees


Docker resolves service names automatically.

Useful Docker Commands
docker compose ps
docker compose logs frontend
docker compose logs backend
docker compose logs mongodb
docker compose down -v
