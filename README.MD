# Hands-On L3: Containers with Docker

This repository contains a Python Flask web app with a Redis cache and a PostgreSQL container, built and run using Docker and Docker Compose.

## Execution Steps
 
### 1. Install Docker Desktop
 
Downloaded and installed Docker Desktop for Windows from the official docs.
 
Verified the install with:
 
```
docker --version
```
 
### 2. Run the Application
 
All files needed to build and run the app (`app.py`, `Dockerfile`, `compose.yaml`, `requirements.txt`) are included in this repository. To run it:
 
1. Clone the repository:
```
   git clone <repo-url>
   cd <repo-folder>
```
 
2. Build and start the containers:
```
   docker compose up
```
 
   This builds the `web` service from the `Dockerfile` (a Flask app on `python:3.12-alpine`, installing dependencies from `requirements.txt`) and starts the `redis` service from the `redis:alpine` image. The `web` service maps host port `8000` to container port `5000` and depends on `redis`.
 
Opened the app in a browser at:
 
```
http://localhost:8000
```
 
Refreshed the page several times and confirmed the hit counter incremented on each request, showing that Redis was correctly persisting state between requests.
 
### 3. Stop the Stack
 
```
docker compose down
```
 

 ## What I Learned
 
- How to pull and run standalone containers (PostgreSQL) versus combining multiple services together with Docker Compose.
- How Docker Compose handles service networking automatically: the Flask app connects to Redis using the service name `redis` as the hostname, with no manual network configuration needed.
- How Docker Desktop on Windows depends on virtualization support and WSL2, and how to diagnose and fix issues when those aren't set up correctly (see Issues tab).

Note: some of the content in this file was drafted with the help of Claude Sonnet 5, then reviewed and edited