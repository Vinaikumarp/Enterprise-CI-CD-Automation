# Enterprise-CI-CD-Automation
End-to-end CI/CD automation using Jenkins, Maven, SonarQube, Nexus, Docker, Trivy, Docker Hub, and Docker Swarm.

## 📌 Project Overview

This project demonstrates an end-to-end CI/CD automation pipeline using Jenkins and various DevOps tools.

The pipeline automatically retrieves source code from GitHub, builds the application using Maven, performs code quality analysis with SonarQube, publishes artifacts to Nexus Repository, builds Docker images, scans images using Trivy, pushes images to Docker Hub, and deploys the application using Docker Swarm.

## 🛠️ Technologies Used

| Technology       | Purpose                     |
| ---------------- | --------------------------- |
| Git              | Version control             |
| GitHub           | Source code management      |
| Jenkins          | CI/CD automation            |
| Maven            | Application build           |
| SonarQube        | Code quality analysis       |
| Nexus Repository | Artifact management         |
| Docker           | Containerization            |
| Trivy            | Container security scanning |
| Docker Hub       | Container image registry    |
| Docker Swarm     | Container orchestration     |
| Linux            | Server environment          |

## 🔄 CI/CD Pipeline
Developer
    ↓
GitHub
    ↓
Jenkins
    ↓
Checkout Source Code
    ↓
Maven Build
    ↓
SonarQube Code Quality Analysis
    ↓
Quality Gate
    ↓
Nexus Repository
    ↓
Docker Image Build
    ↓
Trivy Security Scan
    ↓
Docker Hub
    ↓
Docker Swarm
    ↓
Application Deployment

## 🚀 Jenkins Pipeline Stages

### 1. Code Checkout
Jenkins retrieves the application source code from GitHub.
git 'https://github.com/Vinaikumarp/dockerwebapp.git'

### 2. Application Build
Maven is used to clean and build the application:  mvn clean install

### 3. Code Quality Analysis
SonarQube analyzes the application source code for code quality issues, bugs, vulnerabilities, and maintainability problems.

### 4. Quality Gate
Jenkins waits for the SonarQube Quality Gate result.
If the Quality Gate fails, the pipeline stops.

### 5. Artifact Publishing
The generated WAR file is uploaded to Nexus Repository.
Example artifact:  vprofile-v2.war


### 6. Docker Image Build
Docker images are created for the application and database.
docker build -t appimage:1.0 Docker-app
docker build -t dbimage:1.0 Docker-db

### 7. Trivy Security Scan
Trivy scans the Docker images for known vulnerabilities.
trivy image appimage:1.0
trivy image dbimage:1.0


### 8. Push Images to Docker Hub
After successful scanning, the Docker images are tagged and pushed to Docker Hub.
vinaikumarp/java-app:1.0
vinaikumarp/db-app:1.0


### 9. Docker Swarm Deployment

The application is deployed as a Docker Stack using Docker Swarm.
docker stack deploy myapp --compose-file=compose.yml

## 🐳 Docker

Docker is used to package the application and its dependencies into container images.
The project contains separate Docker configurations for:
Docker-app/
Docker-db/


## 🔐 Security Scanning

Trivy is integrated into the CI/CD pipeline to scan Docker images for security vulnerabilities.

Pipeline flow:


Docker Build
     ↓
Trivy Scan
     ↓
If Scan Successful
     ↓
Push Image


This helps identify vulnerable packages before the images are deployed.

## 📦 Docker Hub
The Docker images are stored in Docker Hub.

### Application Image
vinaikumarp/java-app:1.0

### Database Image
vinaikumarp/db-app:1.0
Docker Hub acts as the container image registry between the CI pipeline and deployment environment.

## 🐝 Docker Swarm Deployment
Docker Swarm is used for container orchestration.
The application is deployed as a Docker Stack using:  docker stack deploy -c compose.yml myapp

### Useful Commands
Check the Swarm stacks:  docker stack ls
Check services:  docker stack services myapp
Check running tasks:  docker stack ps myapp
Remove the stack:  docker stack rm myapp

## 📁 Project Structure

Enterprise-CI-CD-Automation/
│
├── Jenkinsfile
│
├── compose.yml
│
├── Docker-app/
│   └── Dockerfile
│
├── Docker-db/
│   └── Dockerfile
│
├── README.md
│
└── screenshots/

## ⚙️ Jenkins Pipeline Configuration
The Jenkins pipeline requires the following tools and credentials to be configured.

### Jenkins Tools
Maven
Example Maven tool name:
my_maven

### Jenkins Credentials
SonarQube credentials
Nexus credentials
Docker Hub credentials

Credentials should be stored securely in Jenkins Credentials Manager and should not be hardcoded in the repository.

## 🔧 Prerequisites
Before running this project, install and configure:
Linux
Git
Java
Maven
Jenkins
Docker
SonarQube
Nexus Repository
Trivy
Docker Hub Account
Docker Swarm

## ▶️ Deployment
### Initialize Docker Swarm
docker swarm init

### Deploy the Application
docker stack deploy -c compose.yml myapp

### Check the Stack
docker stack ls

### Check Services
docker stack services myapp

### Check Running Tasks
docker stack ps myapp

## 🏗️ Architecture
                   ┌─────────────┐
                   │   GitHub    │
                   └──────┬──────┘
                          │
                          ↓
                   ┌─────────────┐
                   │   Jenkins   │
                   └──────┬──────┘
                          │
             ┌────────────┼────────────┐
             ↓            ↓            ↓
          Maven       SonarQube      Nexus
             │            │            │
             └────────────┼────────────┘
                          ↓
                   Docker Build
                          ↓
                    Trivy Scan
                          ↓
                    Docker Hub
                          ↓
                  Docker Swarm
                          ↓
                  Application


## 🎯 Key DevOps Concepts Demonstrated

This project demonstrates practical knowledge of:
* CI/CD Pipeline
* Git and GitHub
* Jenkins Declarative Pipeline
* Jenkins Credentials
* Maven Build
* SonarQube Code Quality Analysis
* SonarQube Quality Gates
* Nexus Artifact Repository
* Docker Containerization
* Docker Images
* Dockerfile
* Docker Registry
* Trivy Vulnerability Scanning
* Docker Hub
* Docker Compose
* Docker Stack
* Docker Swarm
* Container Orchestration
* Automated Deployment

## 💡 Project Objective
The main objective of this project is to automate the complete application delivery process from source code checkout to production-style container deployment.
The pipeline reduces manual work and provides an automated process for:
Code → Build → Analyze → Package → Scan → Push → Deploy

## 👨‍💻 Author
**P Vinay Kumar**
DevOps / CI-CD Automation Project
