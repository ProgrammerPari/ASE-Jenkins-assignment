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
        C:\\Users\\USER\\AppData\\Local\\Programs\\Python\\Python310\\python.exe -m pip install --upgrade pip
        C:\\Users\\USER\\AppData\\Local\\Programs\\Python\\Python310\\Scripts\\pip.exe install -r requirements.txt
        '''
    }
}


        stage('Test') {
    steps {
        bat 'C:\\Users\\USER\\AppData\\Local\\Programs\\Python\\Python310\\python.exe -m pytest tests/'
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
