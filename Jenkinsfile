pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git ''
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("mypythonapp")
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    dockerImage.run('-d --name your-container-name')
                }
            }
        }
        stage('Show Results') {
            steps {
                script {
                    sh 'docker logs your-container-name'
                }
            }
        }
    }
    post {
        always {
            script {
                sh 'docker stop your-container-name'
                sh 'docker rm your-container-name'
            }
        }
    }
}
