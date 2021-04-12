pipeline {
  agent {
    docker {
      image 'node:7-alpine'
    }
  }
  stages {
    stage('Test') {
      steps {
        echo "whoami: "
        whoami
        hostname
        sh "node --version"
      }
    }
  }
}
