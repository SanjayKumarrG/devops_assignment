pipeline {
  environment {
    dockerimagename = "gsanjaykumar/react-app"
    dockerImage = ""
    SSH_CREDENTIALS = '29cb94cc-a06c-4d03-b406-db05e0550518'
  }
  agent any
  stages {
    stage('Checkout Source') {
      steps {
        script {
          git credentialsId: env.SSH_CREDENTIALS, url: 'git@github.com:SanjayKumarrG/devops_assignment.git'
        }
      }
    }
    stage('Build image') {
      steps{
        script {
          dockerImage = docker.build dockerimagename
        }
      }
    }
    stage('Pushing Image') {
      environment {
        registryCredential = 'dockerhub-credentials'
      }
      steps{
        script {
          docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
            dockerImage.push("latest")
          }
        }
      }
    }
    stage('Deploying React.js container to Kubernetes') {
      steps {
        script {
          kubernetesDeploy(configs: "deployment.yaml", "service.yaml")
        }
      }
    }
  }
  post {
    success {
      echo 'Build successful! Application deployed.'
    }
    failure {
      echo 'Build failed! Take necessary actions.'
    }
  }
}
