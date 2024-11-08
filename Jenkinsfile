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
                    export NPM_CONFIG_PREFIX=~/.npm-global
                    mkdir -p ~/.npm-global
                    npm config set cache ~/.npm-global --global
                    export PATH=$NPM_CONFIG_PREFIX/bin:$PATH
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
