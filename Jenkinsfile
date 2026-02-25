pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/SandhiyaDevi-2002/Docker-Demo.git'
            }
        }

        stage('Build Jar') {
            steps {
                powershell 'mvn clean package -DskipTests'
            }
        }

        stage('Build Docker Image') {
            steps {
                powershell 'docker build -t docker-demo .'
            }
        }

        stage('Stop Old Container') {
            steps {
                powershell 'docker stop docker-demo 2>$null || exit 0'
                powershell 'docker rm docker-demo 2>$null || exit 0'
            }
        }

        stage('Run Container') {
            steps {
                powershell 'docker run -d -p 8081:8080 --name docker-demo docker-demo'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}