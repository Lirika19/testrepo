pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Lirika19/testrepo'
            }
        }
        stage('Setup Environment') {
            steps {
                sh '''
                export DEBIAN_FRONTEND=noninteractive
                sudo apt update
                sudo apt install -y docker.io docker-compose
                sudo systemctl start docker
                sudo systemctl enable docker
                '''
            }
        }
        stage('Deploy Redis Cluster') {
            steps {
                sh '''
                cd testrepo
                docker-compose up -d
                '''
            }
        }
    }
}

