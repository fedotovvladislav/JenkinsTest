pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/fedotovvladislav/JenkinsTest.git'
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'python3 -m venv venv'
                sh 'source venv/bin/activate && pip install -r requirements.txt'
            }
        }

        stage('Run tests') {
            steps {
                sh 'source venv/bin/activate && pytest'
            }
        }
    }

    post {
        always {
            cleanWs() // Очистка рабочей директории
        }
    }
}