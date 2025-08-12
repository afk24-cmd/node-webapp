pipeline {
    agent { label 'linux-agent' } 

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: '9e9a0fb9-968c-407a-812f-1cea6a00b6f3', url: 'https://github.com/afk24-cmd/node-webapp.git', branch: 'main'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("node-webapp:${env.BUILD_NUMBER}")
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    dockerImage.run(-p 3000:3000)
                }
            }
        }
    }
}
