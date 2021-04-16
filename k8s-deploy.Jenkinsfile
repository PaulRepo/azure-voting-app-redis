pipeline {
	agent {
		label 'image-builder'
	}
	stages {
		stage('Check Branch') {
			steps {
				echo "branch ===> ${env.BRANCH_NAME}"
			}
		}
		stage('Approve PROD deploy') {
			when {branch 'master'}
			options {
				timeout(time: 1, unit: 'MINUTES')
			}
			steps {
				input message: 'Deploy?'
			}
			post {
				success {
					echo 'Production Deploy approved'
				}
				aborted {
					echo 'Production Deploy rejected'
				}
			}
		}
		stage('Deploy to production') {
			when {branch 'master'}
			steps {
				script {
					kubernetesDeploy(configs: 'paul-azure-vote-all-in-one-redis.yaml', kubeconfigId: 'mykubeconfig')
				}
			}
		}
	}
}
