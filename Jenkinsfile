pipeline {
	agent any
	environment {
		DOCKER_IMAGE = 'hello-world-java:latest' 
	}
	
	stages {
		stage('Checkout'){
			steps{
				checkout scm
			}
		}
	
		stage('Build') {
			steps {
				sh 'javac HelloWorld.jav'
			}
		}
		stage('Package') {
			steps {
				sh 'jar cf HelloWorld.jar HelloWorld.class'
			}
		}
		stage ('Docker Build') {
			steps {
				sh """
					docker build -t $DOCKER_iMAGE .
			}
		}
	}

		post {
			success {
				echo 'Build completed successfully.'
			}
			failure {
				echo 'Build failed.'
			}

		}
	
}