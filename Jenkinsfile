pipeline {
    agent none

    stages {
        stage('checkout') {
            steps {
                git url: 'https://github.com/dev-Anamul/jenkins-practice.git' branch: 'dev'
            }
        }
        stage('Test') {
            agent {
                docker {
                    image 'node:22'
                }
            }

            steps("Testing web one") {
                step("change directory") {
                    sh 'cd one-web'
                }
                step("install dependencies") {
                    sh 'yarn install'
                }
                step("run tests") {
                    sh 'yarn test'
                }

                post{
                    success {
                        echo "Tests passed for web one"
                    }
                    failure {
                        echo "Tests failed for web one"
                    }
                    always {
                        echo "This will always run"
                    }
                }
            }

            steps("Testing web two") {
                step("change directory") {
                    sh 'cd two-web'
                }
                step("install dependencies") {
                    sh 'yarn install'
                }
                step("run tests") {
                    sh 'yarn test'
                }

                post{
                    success {
                        echo "Tests passed for web two"
                    }
                    failure {
                        echo "Tests failed for web two"
                    }
                    always {
                        echo "This will always run"
                    }
                }
            }

            steps("Testing api one") {
                step("change directory") {
                    sh 'cd one-api'
                }
                step("install dependencies") {
                    sh 'yarn install'
                }
                step("run tests") {
                    sh 'yarn test'
                }

                post{
                    success {
                        echo "Tests passed for web three"
                    }
                    failure {
                        echo "Tests failed for web three"
                    }
                    always {
                        echo "This will always run"
                    }
                }
            }

            steps("Testing api two") {
                step("change directory") {
                    sh 'cd two-api'
                }
                step("install dependencies") {
                    sh 'yarn install'
                }
                step("run tests") {
                    sh 'yarn test'
                }

                post{
                    success {
                        echo "Tests passed for web four"
                    }
                    failure {
                        echo "Tests failed for web four"
                    }
                    always {
                        echo "This will always run"
                    }
                }
            }
        }
        stage('build the apps') {

            agent{
                docker {
                    image 'node:22'
                }
            }

            steps("Building web one") {
                step("change directory") {
                    sh 'cd one-web'
                }
                step("install dependencies") {
                    sh 'yarn install'
                }
                step("build the app") {
                    sh 'yarn build'
                }

                post{
                    success {
                        echo "Build passed for web one"
                    }
                    failure {
                        echo "Build failed for web one"
                    }
                    always {
                        echo "This will always run"
                    }
                }
            }

            steps("Building web two") {
                step("change directory") {
                    sh 'cd two-web'
                }
                step("install dependencies") {
                    sh 'yarn install'
                }
                step("build the app") {
                    sh 'yarn build'
                }

                post{
                    success {
                        echo "Build passed for web two"
                    }
                    failure {
                        echo "Build failed for web two"
                    }
                    always {
                        echo "This will always run"
                    }
                }
            }

            steps("Building api one") {
                step("change directory") {
                    sh 'cd one-api'
                }
                step("install dependencies") {
                    sh 'yarn install'
                }
                step("build the app") {
                    sh 'yarn build'
                }

                post{
                    success {
                        echo "Build passed for web three"
                    }
                    failure {
                        echo "Build failed for web three"
                    }
                    always {
                        echo "This will always run"
                    }
                }
            }

            steps("Building api two") {
                step("change directory") {
                    sh 'cd two-api'
                }
                step("install dependencies") {
                    sh 'yarn install'
                }
                step("build the app") {
                    sh 'yarn build'
                }

                post{
                    success {
                        echo "Build passed for web four"
                    }
                    failure {
                        echo "Build failed for web four"
                    }
                    always {
                        echo "This will always run"
                    }
                }
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