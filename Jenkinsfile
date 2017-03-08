#!groovy

pipeline {
    agent any
    stages {

    	stage('Compare SVN'){
		steps{
	timestamps{		
				echo 'Comparing SVN...'
				echo '${gitName}'
				echo '${dockerRepo}'
				echo '${dockerFileName}'
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
                		git 'https://github.com/Test-Jenkins-Docker/${gitName}'

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
				git 'https://github.com/Test-Jenkins-Docker/${dockerRepo}'
				sh "ls"
				sh "cd target && ls"
				sh "docker info"
				sh "docker build -t ${dockerFileName} ."
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
