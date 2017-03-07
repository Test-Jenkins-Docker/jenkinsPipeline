#!groovy

pipeline {
    agent any
    stages {

    	stage('Compare SVN'){
		steps{
	timestamps{		
				echo 'Comparing SVN...'
				echo env.BRANCH_NAME
				echo env.CHANGE_ID
				script{
					def testing = new org.foo.sharedMethods()
					testing.printHi()
			}	
			}
		}
	}
       	stage('Git and Maven Deploy') {
       		steps {
			timestamps{
                		git 'https://github.com/Test-Jenkins-Docker/testFullPipe.git'

				withMaven(maven: 'M3', mavenSettingsConfig: '43ab0c61-4028-4e36-a268-8928676de664'){
					sh "mvn clean deploy"
				}
				sh "ls"
				sh "cd target && ls"
			}
		}
        }

	stage('Build Docker Container') {
		steps {
			timestamps{
				echo 'Building Docker Container...'
				sh "ls"
				git 'https://github.com/Test-Jenkins-Docker/testDockerFileRepo.git'
				sh "ls"
				sh "cd target && ls"
				sh "docker info"
				sh "docker build -t xactatest ."
				sh "docker images"
			}
        	}
	}
        
	stage('Deploy to Kubernetes') {
		steps {
		timestamps{
        			echo 'Deploying to Kubernetes....'
			}
          	}
        }
    }
    
}
