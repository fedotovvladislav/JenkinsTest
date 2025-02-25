pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/fedotovvladislav/JenkinsTest.git'
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'poetry install --no-root'
            }
        }

        stage('Run tests') {
            steps {
                sh 'poetry run pytest'
            }
        }
    }

    post {
        always {
            cleanWs() // Очистка рабочей директории
        }
    }
}