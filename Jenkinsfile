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
                    sudo chown -R node:node /.npm
                    npm config set cache /workspace/.npm --global
                    npm ci
                    npm run build
                '''
            }
        }
    }
}
