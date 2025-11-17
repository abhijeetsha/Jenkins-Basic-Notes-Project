# Jenkins-Basic-Notes-Project
## ✅ What is Jenkins..?
### Ans: Jenkins is an open-source automation server used to build, test, and deploy applications automatically.
It is one of the most popular tools for CI/CD (Continuous Integration & Continuous Delivery).

## Key Features:-
  * Automates builds and deployments
  * Supports hundreds of plugins (Git, Docker, Kubernetes, Maven, Slack, etc.)
  * Works with pipelines to create automation workflows
  * Free and open-source
  * Runs on Windows, Linux, macOS

## ✅ What is a CI/CD Pipeline?
### A CI/CD Pipeline is a set of automated steps that enable fast and reliable software delivery.

### CI – Continuous Integration
  * Developers push code regularly
  * Code is automatically built, tested, and validated
  * Helps detect errors early

### Example tasks in CI:
  * Compile the code
  * Run unit tests
  * Code quality checks (SonarQube)
  * Build artifacts (JAR, Docker image)

### CD – Continuous Delivery/Deployment
  * Automated process to release the application
  * Deploys to QA, Staging, and Prod environments
  * Reduces manual work

### Example tasks in CD:
  * Deploy to servers
  * Apply configuration
  * Start services/containers

## ✅ What is Jenkins UI, Dashboard, and Jobs?
## 1. Jenkins UI (User Interface)
### This is the web interface where you interact with Jenkins, From the UI you can:
  * Create jobs
  * Configure Jenkins
  * Install plugins
  * View build status

## 2. Jenkins Dashboard
### The dashboard is the homepage you see after logging in, It shows:
  * All jobs/projects
  * Build status (Success/Failed)
  * Build history
  * Manage Jenkins options
  * Node (agent) status

## 3. Jenkins Jobs
### A job is a task that Jenkins performs, 
### Common job types:
  * Freestyle Job → Basic job, easy to configure
  * Pipeline Job → Uses a Jenkinsfile (code-based pipeline)
  * Multi-branch Pipeline → Automatically detects Git branches
  * Folder Jobs → Organize multiple jobs

### A job can:
  * Pull code from Git
  * Build with Maven/Gradle
  * Run tests
  * Create Docker images
  * Deploy applications

## ✅ What is a Declarative Pipeline?
### A Declarative Pipeline is a simple, structured, and user-friendly syntax for writing Jenkins pipelines.
* It uses a predefined structure:
### Example Declarative Pipeline (Jenkinsfile)
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/user/repo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                sh 'echo Deploying application...'
            }
        }
    }
}
