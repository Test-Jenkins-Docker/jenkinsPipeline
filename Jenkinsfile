#!groovy

pipeline {
    agent any

    stages {
    	stage('Compare SVN'){
		steps{
			timestamps{
				echo 'Comparing SVN...'
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
				archiveArtifacts artifacts: 'target/myproject-0.0.1-SNAPSHOT.jar', onlyIfSuccessful: true
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
