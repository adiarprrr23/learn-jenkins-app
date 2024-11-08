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
                    export NPM_CONFIG_PREFIX=$HOME/.npm-global
                    mkdir -p $HOME/.npm-global
                    npm config set cache $HOME/.npm-global --global
                    export PATH=$HOME/.npm-global/bin:$PATH
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
