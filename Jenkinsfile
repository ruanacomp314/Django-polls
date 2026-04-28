pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/ruanacomp314/Django-polls'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t django-polls .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop django-polls || true'
                sh 'docker rm django-polls || true'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d --name django-polls -p 8000:8000 django-polls'
            }
        }
    }
}
