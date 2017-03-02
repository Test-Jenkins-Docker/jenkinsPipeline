#!groovy

pipeline {
    agent any

    stages {
        stage('Git and Maven Deploy') {
            steps {
                echo 'Building..'
		git 'https://github.com/Test-Jenkins-Docker/testFullPipe.git'
		
		withMaven(maven: 'M3'){
			sh "deploy"
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