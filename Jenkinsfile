pipeline {
    agent any

    stages {

        stage('Install') {
            steps {
                sh 'python3 -m venv .venv'
                sh '.venv/bin/python -m pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                sh 'PYTHONPATH=. .venv/bin/pytest --junitxml=test-results.xml'
            }
        }
    }

    post {
        always {
            junit 'test-results.xml'
        }
    }
}