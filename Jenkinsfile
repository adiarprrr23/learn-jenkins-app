pipeline {
    agent any

    stages {
        stage('Clean and Install') {
            steps {
                script {
                    sh '''
                        rm -rf node_modules
                        rm -f package-lock.json
                    '''
                }
            }
        }

        stage('Install Dependencies') {
            agent {
                docker {
                    image "node:18-alpine"
                    reuseNode true
                }
            }
            steps {
                script {
                    sh '''
                        mkdir -p ~/.npm
                        npm config set cache ~/.npm
                        npm install
                    '''
                }
            }
        }

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
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
