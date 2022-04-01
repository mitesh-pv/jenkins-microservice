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
	}
}
