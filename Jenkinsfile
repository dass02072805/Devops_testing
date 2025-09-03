pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'git@github.com:dass02072805/Devops_testing.git',
                    credentialsId: 'github-key'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t my-node-app .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker run -d -p 3000:3000 --name my-node-app my-node-app'
                }
            }
        }
    }
}
