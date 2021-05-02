pipeline {
  agent any
  stages {
    stage('package') {
      steps {
        sh 'mvn clean'
        sh 'mvn package'
      }
    }

  }
  environment {
    PATH = '/usr/local/src/apache-maven-3.8.1/bin'
  }
}