#!groovy

pipeline {
    agent any

    stages {
    	stage('Compare SVN'){
		echo 'Comparing SVN...'
		svn 'https://github.com/Test-Jenkins-Docker/jenkinsPipeline.git'
	}
       	stage('Git and Maven Deploy') {
       		steps {
			timestamps{
	               		echo 'Building...'
				echo pwd()
				git 'https://github.com/Test-Jenkins-Docker/testFullPipe.git'
				
				withMaven(maven: 'M3', mavenSettingsConfig: '43ab0c61-4028-4e36-a268-8928676de664'){
					sh "mvn clean deploy"
				}
				sh "ls"
				sh "cd target && ls"
			}
	            }
        }

	stage('Test') {
		steps {
			timestamps{
	        		echo 'Testing...'
			}
        	}
	}
        
	stage('Deploy') {
		steps {
			timestamps{
        			echo 'Deploying....'
			}
          	}
        }
    }
    
}
