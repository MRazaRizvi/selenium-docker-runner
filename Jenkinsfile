pipeline {
  agent {
    docker {
      image 'docker/compose:1.29.2'
      args '-v /var/run/docker.sock:/var/run/docker.sock'
    }
  }
  stages {
    stage('Start Grid') {
      steps {
        sh "docker-compose -f grid.yaml up -d"
      }
    }

    stage('Run Test') {
      steps {
        sh "docker-compose -f test-suites.yaml up"
      }
    }
  }
      
      post {
        always {
          sh "docker-compose -f grid.yaml down"
          sh "docker-compose -f test-suites.yaml down"
        }
      }
}
