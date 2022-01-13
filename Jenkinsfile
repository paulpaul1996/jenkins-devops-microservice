pipeline {
	agent any
	// agent { docker { image 'maven:3.8.4' } }
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Build') {
			steps {
				echo "Build"
				sh 'mvn --version'
				echo 'docker --version'
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
