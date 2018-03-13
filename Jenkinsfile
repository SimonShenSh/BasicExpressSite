#!groovy

pipeline {
    agent { docker {
        image 'node:7-alpine'
        args '-u root:root -p 3000:3000'
            }
         }
    environment {
        npm_config_cache=npm-cache
            NANE = 'link-live.cn'
            MONGO__URI = 'aaaaaaaaaaaaaaa'
        }

    stages {
        stage('build') {
            steps {
                sh 'npm --version'
                sh 'npm install'
            }
        }

    stage('Test') {
            steps {
                echo 'Testing'
            }
        }

    stage('Sanity check') {
                steps {
                    input "Does the staging environment look ok?"
                }
            }

    stage('Deploy-dev') {
                steps {
                    echo 'Deploying'
                }
            }
    }
    post {
            always {
                echo 'This will always run'
            }
            success {
                echo 'This will run only if successful'
            }
            failure {
                echo 'This will run only if failed'
            }
            unstable {
                echo 'This will run only if the run was marked as unstable'
            }
            changed {
                echo 'This will run only if the state of the Pipeline has changed'
                echo 'For example, if the Pipeline was previously failing but is now successful'
            }
        }
}