pipeline {

  environment {
    dockerimagename = "flofree/duplo-kub"
    dockerImage = ""
  }

  agent any

  stages {

    stage('Build image') {
      steps{
        script {
          dockerImage = docker.build dockerimagename
        }
      }
    }

    stage('Pushing Image') {
      environment {
               registryCredential = 'dockerhub-credential'
           }
      steps{
        script {
          docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
            dockerImage.push("v1")
          }
        }
      }
    }

    stage('Deploying React.js container to Kubernetes') {
      steps {
        script {
          // kubernetesDeploy(configs: "deployment.yaml", "service.yaml") deprecato
          // Applica i file YAML sul cluster Kubernetes utilizzando il plugin senza specificare le credenziali
          sh 'kubectl apply -f deployment.yaml -f service.yaml'
        }
      }
    }

  }

}