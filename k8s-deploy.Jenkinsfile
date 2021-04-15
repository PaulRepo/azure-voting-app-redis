pipeline {
	agent {
		label 'image-builder'
	}
	stages {
		stage('K8S Deploy') {
			steps {
				script {
					kubernetesDeploy(configs: '**/*.yaml', kubeconfigId: 'mykubeconfig')
				}
			}
		}
	}
}
