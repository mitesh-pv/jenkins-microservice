DOCKER_MAVEN_IMAGE = 'maven:3.5.5-jdk-8-alpine'
DOCKER_MAVEN_ARGS = '-v $HOME/.m2:/root/.m2'

pipeline {
	// agent any
	agent {
		docker {
			image DOCKER_MAVEN_IMAGE
			args DOCKER_MAVEN_ARGS
		}
	}
	
	stages {
		stage('Build') {
			steps {
				echo 'Build'
			}
		}

		stage('Test') {
			steps {
				echo 'Test'
			}
		}

		stage('Deploy') {
			steps {
				echo 'Deploy'
			}
		}
	} 
	
	// post activities
	post {
		always {
			echo 'run always'
		}
		success {
			echo 'run on success'
		}
		failure {
			echo 'on failure'
		}
		// unstable - when test failure happens
		// changed - when status of a build changes
	}
}
