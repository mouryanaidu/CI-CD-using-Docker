pipeline {
    agent any
	
	  tools
    {
       maven "Maven"
    }
 stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/mouryanaidus/CI-CD-using-Docker.git'
             
          }
        }
	 stage('Execute Maven') {
           steps {
             
                sh 'mvn package'             
          }
        }
        

  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t samplewebapp:latest .' 
                sh 'docker tag samplewebapp mouryanaidu/samplewebapp:latest'
                //sh 'docker tag samplewebapp mouryanaidu/samplewebapp:$BUILD_NUMBER'
               
          }
        }
     
  stage('Publish image to Docker Hub') {
          
            steps {
        withDockerRegistry([ credentialsId: "mou_dockid", url: "" ]) {
          sh  'docker push mouryanaidu/samplewebapp:latest'
        //  sh  'docker push mourynaidu/samplewebapp:$BUILD_NUMBER' 
        }
                  
          }
        }
     
 } 
