pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', 
                    url: 'git@github.com:dass02072805/Devops_testing.git', 
                    credentialsId: 'GitHub_Devops_Key'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t my-node-app .'
                }
            }
        }

        stage('Deploy Container') {
            steps {
                script {
                    // Stop and remove old container if it exists (running or stopped)
                    sh '''
                        if [ "$(docker ps -aq -f name=my-node-app)" ]; then
                           docker stop my-node-app || true
                           docker rm my-node-app
                        fi
                    '''
                    
                    // Run new container
                    sh 'docker run -d --name my-node-app -p 3000:3000 my-node-app'
                }
            }
        }
    }
}
