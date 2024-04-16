pipeline {
    agent any

    environment {
        NODEJS_VERSION = '12.22.9'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'git@github.com:SanjayKumarrG/devops_assignment.git'
            }
        }

        stage('Installation') {
            tools {
                nodejs NODEJS_VERSION
            }
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm build'
            }
        }
    }

    post {
        success {
            // Actions to perform when the build succeeds
            echo 'Build successful!'
        }
        failure {
            // Actions to perform when the build fails
            echo 'Build failed!'
        }
    }
}

