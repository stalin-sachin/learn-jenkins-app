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
                sh 'npm test'


            }
        }
    }

    post {
        always {
            junit 'test-results/junits.xml'
        }
    }
}