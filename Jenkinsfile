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
              
                sh 'docker build -t bisu:latest .' 
                sh 'docker tag bisu papunabiswal/bisu:$BUILD_NUMBER'
               
          }
        }
  stage('Publish image to Docker Hub') {
            steps {
        withDockerRegistry([ credentialsId: "DockerHub", url: "" ]) {
           sh  'docker push papunabiswal/bisu:$BUILD_NUMBER' 
		}
                  
          }
        }
		
    }
}
