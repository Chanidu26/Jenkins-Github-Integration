pipeline {
    agent any
    environment {
        
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Chanidu26/Jenkins-Github-Integration.git'
            }
        }

        stage('Install Dependencies') {
            steps {
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
                script {
                    sh 'venv\\Scripts\\activate && pytest'
                }
            }
        }
    }
    post {
        always {
            echo 'Cleaning up...'
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
