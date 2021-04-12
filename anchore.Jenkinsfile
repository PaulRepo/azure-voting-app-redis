pipeline {
	agent any
	stages {
		stage('Container scanning') {
			steps {
				sh '''
					echo "paul0docker/jenkinsdocker:v1" > anchore_images
					anchore name: 'anchore_images'
				'''
			}
		}
	}
}
