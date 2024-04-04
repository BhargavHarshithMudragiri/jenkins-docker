pipeline {
    agent any
 
   tools
    {
       maven 'maven394'
    }
 stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/BhargavHarshithMudragiri/jenkins-docker.git'
             
          }
        }
  stage('Execute Maven') {
           steps {
             
                sh 'mvn clean compile package'             
          }
        }
stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t samplewebapp:latest .' 
                sh 'docker tag samplewebapp bhargavharshith/samplewebapp:latest'          
          }
        }
     
  stage('Run Docker container on remote hosts') {
             
            steps {
                withDockerRegistry([ credentialsId: "dockerHubcredentials", url: "" ]) {
          sh  'docker push bhargavharshith/samplewebapp:latest'
            }
        }
    }
 }
