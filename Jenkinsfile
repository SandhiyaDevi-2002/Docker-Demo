pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/SandhiyaDevi-2002/Docker-Demo.git',
                    credentialsId: 'github'
            }
        }

        stage('Build JAR') {
            steps {
                bat 'mvnw.cmd clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t springboot-jenkins-demo .'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d -p 8082:8082 springboot-jenkins-demo'
            }
        }
    }
}