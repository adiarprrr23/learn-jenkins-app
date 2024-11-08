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
                    npm --versionremoving node_modules and package-lock.json if they exist
                    rm -rf node_modules package-lock.json
                    
                    npm ci --verbose
                    
                    npm run build
                    
                    ls -la
                '''
            }
        }
    }
}
