pipeline {
	// agent any
	agent {
		docker {
			image 'maven:3.8.5'
		}
	}
	
	stages {
		stage('Build') {
			steps {
				echo 'Build'
				sh 'mvn --version'
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
