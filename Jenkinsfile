pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Code checked out from GitHub'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Verify Artifact') {
            steps {
                sh 'ls -l build.txt'
            }
        }
    }

    post {
        success {
            echo 'Build executed successfully in Jenkins'
        }
    }
}
