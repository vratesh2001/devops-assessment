![Build Status](https://github.com/vratesh2001/devops-assessment/actions/workflows/main.yml/badge.svg)

# DevOps Assessment - Full Stack Web Application

This project consists of a Django Backend and a React (Vite) Frontend, fully containerized and automated using Docker and GitHub Actions.

## Project Structure
- **/frontend**: React application served via Nginx.
- **/backend**: Django REST API running on Python 3.12.
- **/.github/workflows**: CI/CD pipeline for automated Docker builds.

## How to Run Locally
1. Clone the repository.
2. Run `docker-compose up --build`.
3. Frontend: `http://localhost`
4. Backend: `http://localhost:8000`

## CI/CD Pipeline
- **GitHub Actions**: Automatically builds and pushes Docker images to Docker Hub on every push to the `main` branch.

## Troubleshooting & Bug Fixes

During the containerization process, the following issues from the base repository were identified and resolved:

1. **Path Mismatch Fix**: The original configuration looked for `manage.py` in `/app/core/`, but the file was located in the root `backend/` directory. I updated the `WORKDIR` and `CMD` in the Dockerfile to correctly map the file structure.
2. **Non-Root Security**: Updated the Backend Dockerfile to run as a non-privileged `django` user instead of `root` to follow security best practices.
3. **Frontend Nginx Routing**: Configured Nginx to properly serve the Vite build and proxy API requests to the Django container, resolving "Connection Refused" errors.
4. **CI/CD Integration**: Resolved 403 Permission errors by migrating the remote origin to a personal repository and configuring GitHub Actions Secrets for secure Docker Hub deployment.
