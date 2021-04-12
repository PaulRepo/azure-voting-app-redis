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
					whoami
					ls -l ./scripts/test_container.sh
					chmod u+x ./scripts/test_container.sh
					ls -l ./scripts/test_container.sh
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
		stage('Push container') {
			
			steps {
				echo "Workspace is $WORKSPACE"
				dir("$WORKSPACE/azure-vote") {
					script {
						def REGISTRY_URL = "https://index.docker.io/v1/"
						def USER_NAME = "paul0docker"
						docker.withRegistry("$REGISTRY_URL", 'DockerHub') {
							def image = docker.build("$USER_NAME/jenkins-voting-app:${env.BUILD_ID}")
							image.push()
						}
					}
				}
			}
		}
	}
}
