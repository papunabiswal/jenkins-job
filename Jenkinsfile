pipeline {
    agent any
	

 stages {
      stage('checkout') {
           steps {
             
                git branch: 'main', credentialsId: 'GitHub', url: 'https://github.com/papunabiswal/jenkins-job.git'
             
          }
        }
       

  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t rahul:latest .' 
                sh 'docker tag rahul papunabiswal/testing:$BUILD_NUMBER'
               
          }
        }
  stage('Publish image to Docker Hub') {
            steps {
        withDockerRegistry([ credentialsId: "DockerHub", url: "" ]) {
           sh  'docker push papunabiswal/testing:$BUILD_NUMBER' 
		}
                  
          }
        }
		
    }
}
