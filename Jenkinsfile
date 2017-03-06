#!groovy

pipeline {
    agent any

    stages {
       	stage('Git and Maven Deploy') {
       		steps {
			timestamps{
	               		echo 'Building..'
				pwd()
				git 'https://github.com/Test-Jenkins-Docker/testFullPipe.git'
				
				withMaven(maven: 'M3', mavenSettingsFilePath: '../../settingsJDK.xml'){
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
	        		echo 'Testing..'
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
