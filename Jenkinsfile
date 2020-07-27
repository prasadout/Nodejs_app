	pipeline {
	environment {
		registry = "nani1010/nani"
		registryCredential = 'docker-hub'
		dockerImage = ''
	}

	agent any
	stages {
		stage('Cloning our Git') {
			steps {
				git 'https://github.com/prasadout/Nodejs_app.git'
				}
			}
	stage('Building our image') {
		steps{
			script {
				dockerImage = docker.build registry + ":$BUILD_NUMBER"

				}
				}
			}
	stage('Deploy our image') {
		steps{
			script {
				docker.withRegistry( '', registryCredential ) {
					dockerImage.push()
					}
					}
					}
				}
	}
	}
