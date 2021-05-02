pipeline {
  agent any
  tools{
    maven 'maven3.8.1'
  }
  stages {
    stage('package') {
      steps {
        sh 'mvn clean'
        sh 'mvn package'
      }
    }

  }
}