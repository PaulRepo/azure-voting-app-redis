pipeline {
	agent any
	stages {
		stage('Container scanning') {
			steps {
				sh '''
					# cp /usr/local/bin/trivy /usr/bin/trivy
					# This pipeline will fail if the image it is scanning has vulnerabilities
					trivy  paul0docker/jenkinsdocker:v1
				'''
			}
		}
	}
}
