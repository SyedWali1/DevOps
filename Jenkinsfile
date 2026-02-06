pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/SyedWali1/DevOps.git'
        BRANCH = 'main'
    }

    stages {

        stage('Checkout SCM') {
            steps {
                echo "Checking out code from GitHub..."
                git branch: "${BRANCH}", url: "${REPO_URL}", credentialsId: 'Test'
            }
        }

        stage('Build') {
            steps {
                echo "Running build steps..."
                
                sh 'echo "Build stage executed"'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                
                sh 'echo "Test stage executed"'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploy stage..."
                
                sh 'echo "Deploy stage executed"'
            }
        }

    }

    post {
        always {
            echo "Pipeline finished."
        }
        success {
            echo "Pipeline succeeded!"
        }
        failure {
            echo "Pipeline failed."
        }
    }
}
