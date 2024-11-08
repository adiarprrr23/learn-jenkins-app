pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image "node:18-alpine"
                    args "-u node"
                    reuseNode true
                }
            }
            steps {
                sh '''
                    export NPM_GLOBAL_DIR=/home/node/.npm-global
                    export NPM_CACHE_DIR=/home/node/.npm
                    mkdir -p $NPM_GLOBAL_DIR
                    mkdir -p $NPM_CACHE_DIR

                    npm config set prefix $NPM_GLOBAL_DIR
                    npm config set cache $NPM_CACHE_DIR --global

                    export PATH=$NPM_GLOBAL_DIR/bin:$PATH
                    npm ci
                    npm run build
                '''
            }
        }
    }
}
