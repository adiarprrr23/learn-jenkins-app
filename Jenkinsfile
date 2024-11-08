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
                    rm -rf node_modules package-lock.json
                    ls -la
                    npm ci --verbose
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
