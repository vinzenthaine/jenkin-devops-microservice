pipeline {
	agent any
	//agent { docker { image 'maven:3.6.3'} }
	environment {
		dockerHome = tool 'myDockerYura'
		mavenHome = tool 'myMavenYura'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage ('Build') {
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
		stage ('Test') {
			steps {
				echo "Test"
			}
		}
		stage ('Integration test') {
			steps {
				echo "Integration test"
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