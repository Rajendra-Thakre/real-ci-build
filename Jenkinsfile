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
     // NEW: Archive artifact stage
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
