pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node -v
                    npm -v
                    npm ci
                    npm run build
                    ls -la
                    mkdir -p build
                    touch build/index.html
                    ls -la build/
                    echo "Build Stage..." > build/index.html
            
                '''
            }
        }
        stage('Test') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh  'echo "Test Stage..."'
                sh 'test -f build/index.html'

            }
        }
    }
}