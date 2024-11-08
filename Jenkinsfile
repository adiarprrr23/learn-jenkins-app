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
                    # Set npm cache to a writable directory
                    npm config set cache /workspace/.npm --global
                    
                    # Ensure the cache directory exists
                    mkdir -p /workspace/.npm

                    # Fix permissions for the .npm folder
                    chown -R node:node /workspace/.npm

                    # Install dependencies and run the build
                    npm ci
                    npm run build
                '''
            }
        }
    }
}
