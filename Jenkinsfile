pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                echo 'Cloning repository...'
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'python3 -m venv venv'
                sh '. venv/bin/activate && pip install -r requirements.txt'
            }
        }

        stage('Lint/Format Check') {
            steps {
                echo 'Optional: Add linting here'
            }
        }

        stage('Run App') {
            steps {
                echo 'Optional: Run Flask app here'
            }
        }
    }
}
