pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/midankalahon786/devops-assignment2.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t my-web-app .'
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    sh '''
                        docker stop webapp || true
                        docker rm webapp || true
                        docker run -d --name webapp -p 8081:80 my-web-app
                    '''
                }
            }
        }
    }
}
