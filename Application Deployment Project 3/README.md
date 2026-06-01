# React Application CI/CD Deployment using Docker, Jenkins, AWS & Monitoring

## Project Overview

This project demonstrates the deployment of a React application in a production-ready environment using DevOps best practices.

The application is containerized using Docker, automated through Jenkins CI/CD pipelines, deployed on AWS EC2, and monitored using Uptime Kuma.

---

## Technologies Used

* React
* Docker
* Docker Compose
* Bash Scripting
* Git & GitHub
* Jenkins
* Docker Hub
* AWS EC2 (Ubuntu)
* Uptime Kuma

---

## Project Architecture

GitHub Repository → Jenkins Pipeline → Docker Build → Docker Hub → AWS EC2 Deployment → Monitoring

---

## Repository Structure

```text
devops-react-deployment/
│
├── build/
├── Dockerfile
├── docker-compose.yml
├── build.sh
├── deploy.sh
├── .gitignore
├── .dockerignore
└── screenshots/
```

---

## Docker Configuration

### Build Docker Image

```bash
docker build -t react-app .
```

### Run Container

```bash
docker run -d -p 80:80 --name react-container react-app
```

---

## Docker Compose

### Start Application

```bash
docker-compose up -d
```

### Stop Application

```bash
docker-compose down
```

---

## Bash Scripts

### build.sh

Builds the Docker image.

```bash
#!/bin/bash
docker build -t react-app .
```

### deploy.sh

Deploys the Docker container.

```bash
#!/bin/bash

docker stop react-container || true
docker rm react-container || true

docker run -d -p 80:80 \
--name react-container \
react-app
```

---

## Jenkins CI/CD Pipelines

### DEV Pipeline

Triggered when code is pushed to the **dev** branch.

Pipeline Actions:

* Clone GitHub Repository
* Build Docker Image
* Push Image to Docker Hub DEV Repository
* Deploy Container

Docker Image:

```text
niruban7/dev:v1
```

---

### PROD Pipeline

Triggered when code is pushed or merged to the **main** branch.

Pipeline Actions:

* Clone GitHub Repository
* Build Docker Image
* Push Image to Docker Hub PROD Repository
* Deploy Container

Docker Image:

```text
niruban7/prod:v1
```

---

## Docker Hub Repositories

### DEV Repository

```text
niruban7/dev
```

### PROD Repository

```text
niruban7/prod
```

---

## AWS Deployment

### EC2 Configuration

| Parameter        | Value               |
| ---------------- | ------------------- |
| Instance Type    | t2.micro            |
| Operating System | Ubuntu              |
| Region           | ap-south-1 (Mumbai) |

### Security Group Configuration

| Port | Purpose                 |
| ---- | ----------------------- |
| 80   | Application Access      |
| 8080 | Jenkins                 |
| 3001 | Uptime Kuma Monitoring  |
| 22   | SSH Access (My IP Only) |

---

## Application URL

```text
http://13.203.193.16
```

---

## Jenkins URL

```text
http://13.203.193.16:8080
```

---

## Monitoring

Monitoring is implemented using **Uptime Kuma**.

### Monitoring URL

```text
http://13.203.193.16:3001
```

### Features

* Application Health Monitoring
* Real-Time Status Monitoring
* Downtime Detection
* Notification Support

---

## GitHub Webhook

GitHub Webhooks are configured to trigger Jenkins builds automatically.

Webhook URL:

```text
http://13.203.193.16:8080/github-webhook/
```

---

## Screenshots Included

### Jenkins

* Login Page
* DEV Pipeline Configuration
* PROD Pipeline Configuration
* DEV Build Success
* PROD Build Success

### AWS

* EC2 Instance Details
* Security Group Configuration

### Docker Hub

* DEV Repository
* PROD Repository
* Docker Image Tags

### Deployment

* Running Application Screenshot

### Monitoring

* Uptime Kuma Dashboard
* Health Status Monitoring

---

## Author

**Niruban V**

GitHub:
https://github.com/Niruban-v

Docker Hub:
https://hub.docker.com/u/niruban7

---

## Project Status

* Dockerized Application
* Docker Compose Implemented
* Jenkins CI/CD Configured
* Docker Hub Integration Completed
* AWS Deployment Completed
* Monitoring Configured
* Production Deployment Successful

