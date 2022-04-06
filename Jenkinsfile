pipeline {
	agent any

	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}

	stages {
		stage('Checkout') {
			steps {
				sh 'mvn --version'
				sh 'docker version'
				echo 'Build'
				echo "PATH = $PATH"
				echo "BUILD_NUMBER = $env.BUILD_NUMBER"
				echo "BUILD_ID = $env.BUILD_ID"
				echo "JOB_NAME = $env.JOB_NAME"
				echo "BUILD_TAG = $env.BUILD_TAG"
			}
		}

		stage('Build') {
			steps {
				sh "mvn clean compile"
			}
		}

		stage('Unit Test') {
			steps {
				echo 'Test'
				sh "mvn test"
			}
		}

		stage('Integeration Test') {
			steps {
				echo 'Deploy'
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}

		stage ('Build Docker Image') {
			steps {
				// sh "docker build -t miteshpv96/jenkins-microservices:$env.BUILD_TAG"
				script {
					dockerImage = docker.build("miteshpv96/jenkins-microservices:${env.BUILD_TAG}")
				}
			}
		}

		stage("Package") {
			steps {
				sh "mvn package -DskipTests"
			}
		}

		stage ('Push Docker Image') {
			steps {
				script {
					docker.withRegistry('', 'dockerhub') {
						dockerImage.push();
						dockerImage.push("latest");
					}
				}
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
