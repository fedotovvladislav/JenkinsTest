pipeline {
    agent any

    environment {
        PATH = "$HOME/.local/bin:$PATH"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/fedotovvladislav/JenkinsTest.git'
            }
        }

        stage('Install Poetry') {
            steps {
                sh '''
                curl -sSL https://install.python-poetry.org | python3 -
                poetry --version
                '''
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'poetry install --no-root'
            }
        }

        stage('Run tests') {
            steps {
                sh '''
                export PYTHONPATH=$PYTHONPATH:$(pwd)
                poetry run pytest
                '''
            }
        }
    }

    post {
        always {
            cleanWs() // Очистка рабочей директории
        }
    }
}