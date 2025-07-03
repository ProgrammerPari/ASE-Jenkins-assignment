pipeline {
    agent any

    environment {
        PATH = "C:\\Python311;C:\\Python311\\Scripts;${env.PATH}"
        PYTHONPATH = "."
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Setup') {
            steps {
                bat '''
                python --version
                python -m pip install --upgrade pip
                pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                bat '''
                pytest tests/
                '''
            }
        }

        stage('Done') {
            steps {
                echo '✅ Tests passed.'
            }
        }
    }

    post {
        failure {
            echo '❌ Build failed.'
        }
    }
}
