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
                powershell '''
                docker ps -a --format "{{.Names}}" | Select-String "^docker-demo$"
                if ($?) {
                    docker stop docker-demo
                    docker rm docker-demo
                }
                '''
            }
        }

        stage('Run Container') {
            steps {
                powershell 'docker run -d -p 8082:8082 --name docker-demo docker-demo'
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