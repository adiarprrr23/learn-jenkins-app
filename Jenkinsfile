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
                    rm -rf package-lock.json
                    ls -la
                    npm i
                    npm ci
                    
                    npm run build
                    
                    ls -la
                '''
            }
        }
    }
}
