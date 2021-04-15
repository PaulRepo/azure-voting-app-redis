pipeline {
	agent {
		label 'image-builder'
	}
	stages {
		stage('K8S Deploy') {
			steps {
				script {
					kubernetesDeploy(configs: 'paul-azure-vote-all-in-one-redis.yaml', kubeconfigId: 'mykubeconfig')
				}
			}
		}
	}
}
