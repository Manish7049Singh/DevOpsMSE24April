# Node.js REST API with Docker

![Docker Build and Test](https://github.com/YOUR_USERNAME/nodejs-api/workflows/Docker%20Build%20and%20Test/badge.svg)

A simple Node.js REST API containerized with Docker.

## Prerequisites

- Docker installed on your system
- Docker Compose installed

## Installation

1. Install dependencies (optional, for local development):
```bash
npm install
```

## Docker Commands

### Build the Docker image:
```bash
docker build -t nodejs-api .
```

### Run the container:
```bash
docker run -d -p 8080:8080 --name nodejs-api-container nodejs-api
```

### Using Docker Compose:
```bash
# Start the service in detached mode
docker compose up -d

# Stop the service
docker compose down

# View logs
docker compose logs -f
```

## Testing

Test the health endpoint:
```bash
curl http://localhost:8080/health
```

Expected response:
```json
{ "status": "OK" }
```

## API Endpoints

- `GET /health` - Health check endpoint that returns `{ "status": "OK" }`

## Project Structure

- `index.js` - Main application file
- `Dockerfile` - Docker configuration
- `docker-compose.yml` - Docker Compose configuration
- `package.json` - Node.js dependencies
- `.dockerignore` - Files to exclude from Docker build


## GitHub Actions CI/CD

This project includes a GitHub Actions workflow that automatically:
- Builds the Docker image on every push
- Runs the container
- Tests the /health endpoint
- Displays container logs

The workflow runs on pushes to `main`, `master`, or `develop` branches.

### Workflow File
See `.github/workflows/docker-build.yml` for the complete CI/CD configuration.
