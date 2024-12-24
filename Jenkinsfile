pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo "Cloning repository..."
                git url: 'https://github.com/dev-Anamul/jenkins-practice.git', branch: 'multi-project'
            }
        }

        stage('Test') {
            agent {
                docker {
                    image 'node:22'
                }
            }

            steps {
                echo "Testing web one"
                sh '''
                    cd one-web
                    yarn install
                    yarn lint
                '''
                
                echo "Testing web two"
                sh '''
                    cd two-web
                    yarn install
                    yarn lint
                '''
                
                echo "Testing API one"
                sh '''
                    cd one-api
                    yarn install
                    yarn test
                '''
                
                echo "Testing API two"
                sh '''
                    cd two-api
                    yarn install
                    yarn test
                '''
            }

            post {
                success {
                    echo "Tests passed"
                }
                failure {
                    echo "Tests failed"
                }
            }
        }

        stage('Build the Apps') {
            agent {
                docker {
                    image 'node:22'
                }
            }

            steps {
                echo "Building web one"
                sh '''
                    cd one-web
                    yarn install
                    yarn build
                '''
                
                echo "Building web two"
                sh '''
                    cd two-web
                    yarn install
                    yarn build
                '''
                
                echo "Building API one"
                sh '''
                    cd one-api
                    yarn install
                    yarn build
                '''
                
                echo "Building API two"
                sh '''
                    cd two-api
                    yarn install
                    yarn build
                '''
            }
        }
    }

    post {
        success {
            echo "All tests and builds passed"
        }
        failure {
            echo "Tests or builds failed"
        }
    }
}
