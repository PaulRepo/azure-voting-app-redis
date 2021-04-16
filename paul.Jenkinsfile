pipeline {
	agent {
		label 'image-builder'
	}
	stages {
		stage('Echo-Declarative') {
			steps {
				when {
					branch comparator: 'REGEXP', pattern: '\\W+\\-pipeline'
				}
				echo 'This is a pipeline brnch'
			}
		}
		stage('Echo-Scripted') {
			steps {
				if (env.BRANCH_NAME == 'master') {
					echo 'This is a master branch'
				}
				else {
					echo 'This is NOT the master branch'
				}
			}
		}
	}
}
