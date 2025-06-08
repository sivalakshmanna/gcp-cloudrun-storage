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
		    sh 'ls'	
	            sh 'cd 1-local-storage'	
	            sh 'ls '	
		        sh 'cd 1-local-storage'
                sh  'ls'	
		        sh 'docker build -t sivalakshmanna/siva:${BUILD_NUMBER} .'
                }
            }
        }		
        		
	    stage('Push image to Hub'){
            steps{
                   //sh 'docker login -u sivalakshmanna -p Siva9493@'
		    script{
                   withCredentials([string(credentialsId: 'docker1', variable: 'docker1')]) {
	           sh 'docker login -u sivalakshmanna -p ${docker1}'
		   }
                   sh 'docker push sivalakshmanna/siva:${BUILD_NUMBER}'
                   sh 'docker run -d -p 7000:8080 sivalakshmanna/siva:${BUILD_NUMBER}'
                }
            }
        }
		
      
    }
   
}

