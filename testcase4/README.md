# Node.js REST API with Docker

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
