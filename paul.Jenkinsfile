@Library(github.com/PaulRepo/demo_shared_pipeline) _

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
