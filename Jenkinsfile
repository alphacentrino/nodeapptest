pipeline {
environment{
  dimagename = "rdocker11/nodeapp"
  dimage = ""
}

agent any

stages{
   // Workspce Clean Up 
    stage('workspace Cleanup:'){
        steps{
            
            cleanWs()
        }
    }
    
    // Checkout stage
    
 
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




}


}