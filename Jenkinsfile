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
                    # Create npm global and cache directories in the workspace
                    mkdir -p /workspace/.npm-global
                    mkdir -p /workspace/.npm

                    # Set npm global prefix and cache paths
                    npm config set prefix /workspace/.npm-global
                    npm config set cache /workspace/.npm --global

                    # Change ownership to the non-root user (e.g., 'node')
                    chown -R node:node /workspace/.npm-global /workspace/.npm

                    # Add npm global bin to PATH
                    export PATH=/workspace/.npm-global/bin:$PATH

                    # Install dependencies and build the project
                    npm ci
                    npm run build
                '''
            }
        }
    }
}
