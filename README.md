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
### 🔥 Key Features of Declarative Pipelines
  * More readable and user friendly
  * Follows a fixed structure (pipeline → agent → stages → steps)
  * Easy to validate and debug
  * Supports automated build, test, deploy sequences

### ⭐ Summary Table
| Topic                    | Meaning                                          |
| ------------------------ | ------------------------------------------------ |
| **Jenkins**              | Automation server for CI/CD                      |
| **CI/CD Pipeline**       | Automated build, test & deploy process           |
| **Jenkins UI**           | Web interface of Jenkins                         |
| **Jenkins Dashboard**    | Homepage showing jobs & status                   |
| **Jenkins Jobs**         | Tasks that Jenkins runs                          |
| **Declarative Pipeline** | Code-based structured pipeline using Jenkinsfile |

## ✅ What is a Jenkins Agent (Multi-Node Setup)?
### Jenkins works on a Master–Agent (Controller–Node) architecture.

## 1. Jenkins Controller (Master)
  * Main server
  * Holds Jenkins UI, jobs, plugins 
  * Controls the entire system
  * Does not execute heavy workloads ideally

## 2. Jenkins Agent (Node)
### A Jenkins Agent is a separate machine that performs the actual work (build, test, deploy).
### Agents can be:
  * Linux servers
  * Windows machines
  * Docker containers
  * Kubernetes pods
  * Virtual machines

## ✅ Why Use Multiple Agents (Multi-Nodes)?
### Multiple agents allow:
  * Parallel execution of builds
  * Load balancing
  * Different environments for different projects
  * Faster CI/CD
  * Separation of workloads (e.g., Java builds on Linux, .NET builds on Windows)

### Example:-
| Agent Name     | OS             | Purpose                    |
| -------------- | -------------- | -------------------------- |
| agent-linux-01 | Linux          | Maven/Java builds          |
| agent-win-01   | Windows        | .NET builds                |
| agent-docker   | Linux          | Docker image builds        |
| agent-k8s      | Kubernetes Pod | On-demand ephemeral builds |

## 🔌 How Agents Connect
### Agents connect to the controller using:
  * SSH
  * JNLP
  * Docker
  * Kubernetes plugin
  * Cloud agents (AWS EC2, Azure VM, GCP)

## 🧱 How Jenkins Pipeline Uses Agents
### Example:-
    pipeline {
        agent { label 'linux' }
    
    stages {
        stage('Build') {
            steps {
                sh 'mvn package'
            }
        }
    }
}
