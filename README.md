# Jenkins + Docker CI/CD Pipeline for PHP Web Application

## Project Overview

This project demonstrates an end-to-end **CI/CD pipeline** using **Jenkins**, **Docker**, and **GitHub** for automated deployment of a PHP web application.

The source code was initially cloned from the Edureka project repository and configured into a personal GitHub repository for pipeline automation.

---

## Tech Stack

* Jenkins (Dockerized)
* Docker
* GitHub
* PHP
* Apache
* PowerShell
* WSL Ubuntu

---

## Project Workflow

```text
GitHub Repository
        ↓
Jenkins Pipeline
        ↓
Docker Image Build
        ↓
Docker Container Deployment
        ↓
PHP Application Live on Browser
```

---

## Pipeline Stages

### 1. Clone Repository

Jenkins pulls the latest source code from GitHub.

### 2. Build Docker Image

Docker builds the image using the Dockerfile.

### 3. Deploy Container

The PHP application is deployed inside a Docker container.

---

## Dockerfile Used

```dockerfile
FROM php:7.4-apache
COPY website/ /var/www/html/
EXPOSE 80
```

---

## Jenkins Pipeline Script

```groovy
pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/Pratik-dev07/php-cicd-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t php-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f php-container || true
                docker run -d -p 9090:80 --name php-container php-app
                '''
            }
        }
    }
}
```

---

## How to Run

### Clone Repository

```bash
git clone https://github.com/Pratik-dev07/php-cicd-project.git
cd php-cicd-project
```

### Build Docker Image

```bash
docker build -t php-app .
```

### Run Container

```bash
docker run -d -p 9090:80 --name php-container php-app
```

---

## Access Application

Open in browser:

```text
http://localhost:9090
```

---

## Screenshots

* Jenkins Pipeline Success
* Docker Running Containers
* PHP Website Running
* GitHub Repository

---

## Author

**Pratik Singare**

