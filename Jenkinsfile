pipeline {
  environment {
    dockerimagename = "gsanjaykumar/react-app"
    dockerImage = ""
  }
  agent any
  stages {
    stage('Checkout Source') {
      steps {
        script {
          git 'https://github.com/SanjayKumarrG/devops_assignment.git'
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
          kubernetesDeploy(configs: "deployment.yaml", "service.yaml", kubeconfigId: "mykubeconfig")
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
