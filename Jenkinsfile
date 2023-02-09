pipeline {
    agent any
	

 stages {
      stage('checkout') {
           steps {
             
                git branch: 'main', url: 'https://github.com/papunabiswal/devops-practical-2.git'
             
          }
        }
       

  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t devops11class:latest .' 
                sh 'docker tag devops11class papunabiswal/devops11class:$BUILD_NUMBER'
               
          }
        }
  stage('Publish image to Docker Hub') {
            steps {
        withDockerRegistry([ credentialsId: "DockerHub", url: "" ]) {
           sh  'docker push papunabiswal/devops11class:$BUILD_NUMBER' 
		}
                  
          }
        }
		
    }
}
