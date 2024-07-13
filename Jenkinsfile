pipeline {
    agent {
        label 'AGENT-1'
    }
    options {
        timeout(time: 30, unit: 'MINUTES')
        disableConcurrentBuilds()
        ansiColor('xterm')
    }
    environment {
        APP_VERSION = '' // Variable declaration
    }
    stages {
        stage('Read the Version') {
            steps {
                script {
                    def packageJson = readJSON file: 'package.json'
                    env.APP_VERSION = packageJson.version
                    echo "Application version: ${env.APP_VERSION}"
                }
            }
        }
        stage('Install Dependencies') {
            steps {
                sh """
                npm install
                ls -ltr
                echo "Application version: ${env.APP_VERSION}"
                """
            }
        }
        stage('Build') {
            steps {
                sh """
                zip -q -r backend-${env.APP_VERSION}.zip * -x Jenkinsfile -x backend-${env.APP_VERSION}.zip
                ls -ltr
                """
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
            deleteDir()
        }
        success { 
            echo 'I will run when pipeline is successful'
        }
        failure { 
            echo 'I will run when pipeline fails'
        }
    }
}
