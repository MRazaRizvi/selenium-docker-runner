pipeline {
  agent {
    docker {
      image 'my-jenkins-with-compose'
      args '-v /var/run/docker.sock:/var/run/docker.sock'
    }
  }
  stages {
    stage('Run Test') {
      steps {
        sh 'docker-compose up'
      }
    }
  }
}
