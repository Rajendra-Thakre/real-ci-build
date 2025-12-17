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
     // NEW: Archive artifact stage
        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'build.txt', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build executed successfully in Jenkins'
        }
    }
}
