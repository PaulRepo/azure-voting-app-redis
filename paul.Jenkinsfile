pipeline {
	agent {
		label 'image-builder'
	}
	stages {
		stage('Verify Branch') {
			steps {
				echo "$GIT_BRANCH"
			}
		}
		stage('Docker build') {
			steps {
				sh(script: """
					cd azure-vote/
					docker images
					docker build -t azure-vote-front .
					docker images
					cd ../
				""")
			}
		}
		stage('Start test app') {
			steps {
				sh '''
					docker-compose up -d
					./scripts/test_container.sh
				'''
			}
			post {
				success {
					echo "App started successfully"
				}
				failure {
					echo "App failed to start"
				}
			}
		}
		stage('Run tests') {
			steps {
				sh 'pytest ./tests/test_sample.py'
			}
		}
		stage('Stop test app') {
			steps {
				sh 'docker-compose down'
			}
		}
	}
}
