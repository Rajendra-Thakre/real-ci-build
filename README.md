# 🚀 real-ci-build

A **CI/CD pipeline** built using **Jenkins Declarative Pipeline** to automate code deployment and artifact management.  
This project demonstrates automated **build, deploy, and artifact archiving** processes.

---

## 🛠️ Technologies & Tools Used

| Tool | Description |
|------|-------------|
| ![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white) | CI/CD automation server |
| ![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white) | Version control |
| ![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black) | Deployment environment |
| ![Shell](https://img.shields.io/badge/Shell-4EAA25?style=for-the-badge&logo=gnu-bash&logoColor=white) | Shell scripting for deployment |
| ![Azure](https://img.shields.io/badge/Azure-0078D4?style=for-the-badge&logo=microsoft-azure&logoColor=white) | Cloud deployment / management |
| ![CCNA](https://img.shields.io/badge/CCNA-1DA1F2?style=for-the-badge&logo=network&logoColor=white) | Networking fundamentals (Cisco Certified) |

---

## 🏗️ Pipeline Overview

This Jenkins pipeline automates **code deployment** and **artifact management**.

### **Stages**

1. **Checkout**
   - Prints a message (replace with actual GitHub checkout using `checkout scm`).

2. **Deploy**
   - Deletes old files from `/opt/app/`.
   - Copies latest code from workspace to `/opt/app/`.
   - Creates `deploy.txt` with deployment timestamp.

3. **Archive Artifact**
   - Archives `build.txt` in Jenkins with fingerprint tracking.

---

## 📄 Jenkinsfile

```groovy
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Code checked out from GitHub'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                rm -rf /opt/app/*
                cp -r * /opt/app/
                echo "Deployed at $(date)" > /opt/app/deploy.txt
                '''
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'build.txt', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'CI/CD pipeline executed successfully'
        }
    }
}


