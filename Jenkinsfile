pipeline {
	agent any
	// agent { docker { image 'maven:3.8.4' } }
	stages {
		stage('Build') {
			steps {
				// sh 'mvn --version'
				echo "Build"
				echo "$PATH"
				echo "$BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
				echo "JENKINS_URL - $JENKINS_URL"
			}
		}
		stage('Test') {
			steps {
				echo "Test"
			}
		}
		stage('Integration Test') {
			steps {
				echo "Integration Test"
			}
		}
	} 
	
	post {
		always {
			echo 'I run always'
		} 
		success {
			echo 'I run on your success'
		}
		failure {
			echo 'I run when you fail'
		}
	}

}
