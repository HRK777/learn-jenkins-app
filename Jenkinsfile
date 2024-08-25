pipeline {
    agent {
        docker {
            image 'node:18-alpine'
            reuseNode true
        }
    }
    stages {
        stage('build') {
            steps {
                sh '''
                    ls -la 
                    node -v
                    npm -v
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }

        stage('test') {
            steps {
                sh '''
                    echo 'Test stage'

                    if [ -e src/index.html ]; then
                        echo 'src/index.html exists'
                    else
                        echo 'src/index.html not found'
                        exit 1
                    fi

                '''
            }
        }
    }
}