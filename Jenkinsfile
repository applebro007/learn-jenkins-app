pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:latest'
                    args '--privileged -v /var/run/docker.sock:/var/run/docker.sock'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Test stage'
            }
        }
    }
}
