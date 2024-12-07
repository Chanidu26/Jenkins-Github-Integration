pipeline {
    agent any

    environment {
        
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from GitHub
                git branch: 'main', url: 'https://github.com/Chanidu26/Jenkins-Github-Integration.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Create a virtual environment and install dependencies 
                script {
                    if (!fileExists('venv')) {
                        sh 'python -m venv venv'
                    }
                    sh 'venv\\Scripts\\activate && pip install -r requirements.txt'
                }
            }
        }

        stage('Run Tests') {
            steps {
                // Run tests using pytest
                script {
                    sh 'venv\\Scripts\\activate && pytest'
                }
            }
        }

    }

    post {
        always {
            // Clean up after the build, e.g., deactivate virtual environment
            echo 'Cleaning up...'
        }
        success {
            // Notify on successful build (if required)
            echo 'Build succeeded!'
        }
        failure {
            // Notify on failed build (if required)
            echo 'Build failed.'
        }
    }
}
