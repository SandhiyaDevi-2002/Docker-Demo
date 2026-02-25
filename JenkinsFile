pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Build Stage Running'
            }
        }

        stage('Docker Build') {
            steps {
                echo 'Docker Image Build Stage'
                bat 'docker build -t docker-demo .'
            }
        }

        stage('Run Container') {
            steps {
                echo 'Running Docker Container'
                bat 'docker run -d -p 8080:8080 docker-demo'
            }
        }
    }
}