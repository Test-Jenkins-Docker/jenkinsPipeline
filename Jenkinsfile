#!groovy

pipeline {
    agent any

    timestamps{
    	stages {
        	stage('Git and Maven Deploy') {
            		steps {
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
        	stage('Test') {
	            steps {
	                echo 'Testing..'
        	    }
	        }
        	stage('Deploy') {
	            steps {
        	        echo 'Deploying....'
          	  }
        	}
    	}
    }
}
