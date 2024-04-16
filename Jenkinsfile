pipeline {
    agent {
    	label 'tests'
    }
    stage('Build') {
            steps {
                sh 'npm install'
            }
        }
    stages {
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
