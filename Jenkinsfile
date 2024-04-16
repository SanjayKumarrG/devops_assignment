pipeline {
    agent {
    	label 'tests'
    }
    stages {
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
