  pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                echo 'scm git'
                git branch: 'main', url: 'https://github.com/sivalakshmanna/gcp-cloudrun-storage.git'
            }
        }
        
       
        stage('Build docker image'){
            steps{
                script{
                    echo 'docker image build'
	            sh 'cd 1-local-storage'		
		    sh 'sudo docker build -t sivalakshmanna/siva:${BUILD_NUMBER} .'
                }
            }
        }		
        		
	    stage('Push image to Hub'){
            steps{
                script{
                   withCredentials([string(credentialsId: 'dockerhub', variable: 'dockerhub')]) {
                   sh 'docker login -u sivalakshmanna -p ${dockerhub}'

              }
                   sh 'docker push sivalakshmanna/siva:${BUILD_NUMBER}'
                   sh 'docker run -d -p 7000:8080 sivalakshmanna/siva:${BUILD_NUMBER}'
                }
            }
        }
		
      

   
}

