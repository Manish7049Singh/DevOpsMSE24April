# Node.js API - CI/CD Pipeline

![Deploy Pipeline](https://github.com/YOUR_USERNAME/nodejs-api/workflows/Deploy%20Pipeline/badge.svg)

A Node.js REST API with automated CI/CD pipeline using GitHub Actions.

## Project Overview

This project demonstrates a complete CI/CD pipeline that:
- Automatically triggers on every push to the `main` branch
- Installs dependencies
- Builds a Docker image
- Simulates deployment

## Prerequisites

- Node.js 18 or higher
- Docker (for local testing)
- Git

## Installation

```bash
npm install
```

## Running Locally

```bash
npm start
```

The server will start on `http://localhost:8080`

## API Endpoints

- `GET /health` - Health check endpoint
  - Returns: `{ "status": "OK" }`

## Docker

### Build the image:
```bash
docker build -t nodejs-api .
```

### Run the container:
```bash
docker run -d -p 8080:8080 nodejs-api
```

## CI/CD Pipeline

The GitHub Actions workflow (`.github/workflows/deploy.yml`) includes the following steps:

1. **Check out the repository code** - Clones the repository
2. **Set up Node.js version 18** - Configures Node.js environment
3. **Install project dependencies** - Runs `npm install`
4. **Build the Docker image** - Creates Docker image tagged as `nodejs-api`
5. **Print deployment message** - Displays "Deploying application to server..."

### Workflow Trigger

The pipeline automatically runs on every push to the `main` branch.

### Viewing Pipeline Results

1. Navigate to your GitHub repository
2. Click on the "Actions" tab
3. View the latest workflow run
4. All steps should show a green checkmark ✅

## Git Setup

To push this project to GitHub:

```bash
# Initialize git repository
git init

# Add all files
git add .

# Create initial commit
git commit -m "This is the new CI/CD pipeline for CA2"

# Add remote repository (replace with your repo URL)
git remote add origin https://github.com/YOUR_USERNAME/nodejs-api.git

# Push to main branch
git branch -M main
git push -u origin main
```

## Project Structure

```
.
├── .github/
│   └── workflows/
│       └── deploy.yml       # CI/CD pipeline configuration
├── index.js                 # Main application file
├── Dockerfile              # Docker configuration
├── .dockerignore           # Docker ignore rules
├── .gitignore              # Git ignore rules
├── package.json            # Node.js dependencies
└── README.md               # This file
```

## Expected Outcome

After pushing to GitHub:
- The workflow file `.github/workflows/deploy.yml` is present in the repository
- GitHub Actions run shows all 5 steps completing successfully
- The final step prints "Deploying application to server..." in the logs
- All steps display a green checkmark indicating success
