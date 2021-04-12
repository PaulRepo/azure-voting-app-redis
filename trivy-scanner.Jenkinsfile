pipeline {
	agent any
	stages {
		stage('Container scanning') {
			steps {
				sh '''
					trivy paul0docker/jenkinsdocker:v1
				'''
			}
		}
	}
}
