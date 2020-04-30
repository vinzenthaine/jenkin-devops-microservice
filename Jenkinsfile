pipeline {
	agent any
	//agent { docker { image 'maven:3.6.3'} }
	environment {
		dockerHome = tool 'myDockerYura'
		mavenHome = tool 'myMavenYura'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage ('Checkout') {
			steps {
				echo "==============="
				echo "==============="
				echo "Docker version:"
				echo "==============="
				echo "==============="
				sh "docker version"
				echo "==============="
				echo "==============="
				echo "Maven version:"
				echo "==============="
				echo "==============="
				sh "mvn --version"
			}
		}
		stage ('Compile') {
			steps {
				sh "mvn clean compile"
			}
		}
		stage ('Test') {
			steps {
				sh "mvn test"
			}
		}
		stage ('Integration test') {
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}
		stage ('Package') {
			steps {
				sh "mvn package -DskipTests"
			}
		}

		stage ('Build docker image') {
			steps {
				//sh "docker build -t in28min/currency-exchange-devops:${env.BUILD_TAG}"
				script {
					dockerImage = docker.build("yurabu/currency-exchange-devops:${env.BUILD_TAG}");
				}
			}
		}

		stage ('Push docker image') {
			steps {
				script {
					docker.withRegistry('','dockerhubuser')
					{
						dockerImage.push();
						dockerImage.push("latest");
					}
				}
			}
		}
	} 

	post {
		always {
			echo 'Awesome! I run always'
		}
		success {
			echo 'Success!'
		}
		failure {
			echo 'failure!'
		}
	}
}