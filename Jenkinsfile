pipeline {
	agent any
	
	stages {
		stage('Build') {
			steps {
				echo 'Build'
			}
		}

		stage('Test') {
			steps {
				echo 'Tets'
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
