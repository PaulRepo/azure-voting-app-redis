@Library('github.com/devbyaccident/demo-shared-pipeline') _

pipeline {
	agent any
	stages {
		stage('Call library Hello-World function') {
			steps {
				script {
					helloworld()
				}
			}
		}
	}
}
