pipeline {
	agent any
	stages {
		stage('container scanning') {
			parallel {
				stage('Hello World') {
					steps {
						echo "Hello World !!"
						sleep(time:30, unit: "SECONDS")
					}
				}
				stage('GoodBye World') {
					steps {
						echo "Goodbye World !!"
						sleep(time:30, unit: "SECONDS")
					}
				}
			}
		
		}
	}
}


###############

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
					docker-compose up
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
