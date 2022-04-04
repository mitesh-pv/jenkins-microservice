pipeline {
	// agent any
	agent { 
		docker { 
					image 'maven:3.8.1-adoptopenjdk-11'
          args '-v $HOME/.m2:/root/.m2'
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
