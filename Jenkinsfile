// pipeline {
//     agent any

//     environment {
//         REPO_URL = 'https://github.com/SyedWali1/DevOps.git'
//         BRANCH = 'main'
//     }

//     stages {

//         stage('Checkout SCM') {
//             steps {
//                 echo "Checking out code from GitHub..."
//                 git branch: "${BRANCH}", url: "${REPO_URL}", credentialsId: 'Test'
//             }
//         }

//         stage('Build') {
//             steps {
//                 echo "Running build steps..."
                
//                 sh 'echo "Build stage executed"'
//             }
//         }

//         stage('Test') {
//             steps {
//                 echo "Running tests..."
                
//                 sh 'echo "Test stage executed"'
//             }
//         }

//         stage('Deploy') {
//             steps {
//                 echo "Deploy stage..."
                
//                 sh 'echo "Deploy stage executed"'
//             }
//         }

//     }

//     post {
//         always {
//             echo "Pipeline finished."
//         }
//         success {
//             echo "Pipeline succeeded!"
//         }
//         failure {
//             echo "Pipeline failed."
//         }
//     }
// }
pipeline {
    agent any

    environment{
        GITHUB_CREDS = credentials('Test')
        REPO_URL = 'https://github.com/SyedWali1/DevOps.git'
        BRANCH = 'main'
    }

    stages {
        stage('Checkout SCM') {
            steps {
                git branch: "${BRANCH}", url: "${REPO_URL}", credentialsId: 'github-creds'
            }
        }

        stage('Build') {
            steps{
                echo "Building project.."

            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                sh 'echo "Test Passed"'
            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh 'echo "Updated from Jenkins at $(date)" >> sample.txt'

                    sh 'git config user.email "wali.haider@9to5digitalsolutions.com"'
                    sh 'git config user.name "SyedWali1"'

                    sh 'git add sample.txt'
                    sh 'git commit -m "Automated update from Jenkins" || echo "No changes to commit"'

                    sh "git push https://${GITHUB_CREDS_USR}:${GITHUB_CREDS_PSW}@github.com/SyedWali1/DevOps.git ${BRANCH}"
                }
            }
        }
    }
    post {
        always {
            echo 'Pipeline finished.'
        
        }
    }
}