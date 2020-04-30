pipeline {
	agent { docker { image 'maven:3.6.3'} }
	stages {
		stage ('Build') {
			steps {
				sh "mvn --version"
				echo "Build"
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