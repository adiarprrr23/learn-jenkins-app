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
                    npm config set prefix /workspace/.npm-global
                    npm config set cache /workspace/.npm --global

                    mkdir -p /workspace/.npm-global
                    mkdir -p /workspace/.npm
                    chown -R node:node /workspace/.npm-global /workspace/.npm

                    npm ci
                    npm run build
                '''
            }
        }
    }
}
