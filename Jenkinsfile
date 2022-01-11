pipeline {
environment{
  dimagename = "rdocker11/nodeapp"
  dimage = ""
}

agent any
stages{
// SCM Checkout Stage
/*
    stage('Git-Checkout:'){
      steps{
          // git 'https://github.com/alphacentrino/nodeapp_test.git'
          checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [[$class: 'CleanBeforeCheckout']], userRemoteConfigs: [[url: 'https://github.com/alphacentrino/nodeapp_test.git']]])
  //    }
  //  }
*/
// Build Image
    stage('Build Image:'){
      steps{
          script {
            dimage = docker.build dimagename
          }
      }
    }
// Push Image to Docker Hub
    stage('Push Image to DockerHub:'){
      environment {
        dcreds = 'dockerhublogin'
      }
      steps{
        script {
          docker.withRegistry('https://registry.hub.docker.com', dcreds )
          {
            dimage.push()
          }
        }
          
      }
    }

// Deploy to Kubernetes
/*
    stage('Deploy to Kubernetes:'){
      steps{
          script {
            kubernetesDeploy(configs: "deploymentservice.yml", kubeconfigId: "kubernetes")
          }
      }
    }
    */


}


}