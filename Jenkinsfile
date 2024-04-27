pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/TayyabQ/SCD_Lab10.git'
            }
        }

        stage('Dependency Installation') {
            steps {
                sh 'npm install'  
            }
        }

        stage('Build') {
            steps {
                 docker.build name: 'tayyabqaisar/lab10:${env.BUILD_ID}',
                             file: 'Dockerfile'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
                echo'Tests run successfully'
            }
        }

        stage('Containerized') {
            steps {
                script {
                    sh 'docker build -t lab10:latest .'
                }

                sh 'docker-compose up'
            }
        }
    }
}
