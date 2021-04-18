@Library('github/PaulRepo/demo_shared_pipeline') _

pipeline {
	agent any
	stages {
		stage('Call library function with arguments') {
			steps {
				script {
					helloArgs('Jenkins')
					helloArgs.goodbyeWorld('Jenkins2')
				}
			}
		}
	}
	
}
