pipeline {
	agent any
	// agent { docker { image 'maven:3.8.4' } }
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Checkout') {
			steps {
				echo "Build"
				sh 'mvn --version'
				sh 'docker --version'
			}
		}
		stage('Compile') {
			steps {
				sh "mvn clean compile"
			}
		}
		stage('Test') {
			steps {
				sh "mvn test"
			}
		}
		stage('Integration Test') {
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}
		stage('Package') {
			steps {
				sh "mvn package -DskipTests"
			}
		}
		stage('Build Docker Image') {
			steps {
				// docker build -t in28min/currency-exchange-devops:$BUILD_TAG
				script {
					dockerImage = docker.build("paulpaul1996/currency-exchange-devops:${BUILD_TAG}");
				}
			}
		}
		stage('Push Docker Image') {
			steps {
				script {
					docker.withRegistry('', 'dockerhub') {
						dockerImage.push();
						dockerImage.push('latest');
					}

				}
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
