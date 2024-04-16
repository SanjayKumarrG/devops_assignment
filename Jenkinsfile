pipeline {
    agent {
    	label 'tests'
    }

    environment {
        NODEJS_VERSION = '12.22.9'
    }

    stages {

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
