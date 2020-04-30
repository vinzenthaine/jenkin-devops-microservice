pipeline {
	agent any
	stages {
		stage ('Build') {
			steps {
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