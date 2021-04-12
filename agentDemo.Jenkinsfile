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
        sh 'whoami'
        sh 'hostname'
        sh "node --version"
      }
    }
  }
}
