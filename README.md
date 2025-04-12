# Node.js CI/CD Pipeline using Jenkins and Docker

This project showcases a basic CI/CD setup using **Jenkins** and **Docker** for a Node.js application.

## Overview

- **Application**: Node.js (`app.js`)
- **CI/CD Tools**: Jenkins, Docker
- **Pipeline Definition**: `Jenkinsfile`
- **Containerization**: `Dockerfile`
- **Version Control**: GitHub

## Features

- Automated pipeline with Jenkins
- Docker image build and container deployment
- Clear stages: Install → Build → Deploy
- Git-triggered pipeline execution

## Project Structure

```
.
├── app.js               # Node.js application
├── package.json         # Dependency file
├── Dockerfile           # Docker configuration
├── Jenkinsfile          # Jenkins pipeline definition
├── .github/workflows/   # GitHub Actions (optional)
│   └── main.yml
└── README.md            # Project documentation
```

## Jenkins Pipeline Stages

1. **Clone Repository** – Retrieves the latest codebase
2. **Install Dependencies** – Executes `npm install`
3. **Build Docker Image** – Builds image using Dockerfile
4. **Deploy Container** – Runs app container on port 3000

## Prerequisites

- Jenkins instance (local/cloud)
- Docker installed and running
- GitHub repository setup with this codebase
- Webhook or Poll SCM configuration in Jenkins

## Execution Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/Bsrikanth008/nodejs-web-app.git
   ```

2. **Configure Jenkins Job**
   - Create a new pipeline job
   - Use "Pipeline script from SCM"
   - Set GitHub repository URL
   - Jenkins auto-triggers on changes

3. **Run Locally (Optional)**
   ```bash
   docker build -t my-node-app .
   docker run -d -p 3000:3000 my-node-app
   ```

## Author

Created as part of the **Elevate Labs DevOps Internship** by Srikanth Berla.

## License

This project is intended for educational purposes.
