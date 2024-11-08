pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image "node:18-alpine"
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    mkdir -p ~/.npm-global
                    npm config set cache ~/.npm-global --global
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
