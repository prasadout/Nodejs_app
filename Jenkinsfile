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
	stage ('Stop previous image'){
		steps{
			sh 'docker stop `docker ps -aqf "name=silly_haibt"`'
		}
	}
	stage ('Run latest image'){	
		steps{
			sh 'docker run -itd -p80:3000 nani1010/nani":$BUILD_NUMBER" '
		}
	}
	}
	}
