pipeline {
    agent {
    	label 'tests'
    }

    stages {
    	stage('Installation') {
            steps {
                // Install project dependencies
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'
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
