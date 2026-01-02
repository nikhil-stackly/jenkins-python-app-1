pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                echo 'Code pulled from GitHub'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-python-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker rm -f jenkins-python-container || true
                docker run -d -p 5000:5000 --name jenkins-python-container jenkins-python-app
                '''
            }
        }
    }
}
