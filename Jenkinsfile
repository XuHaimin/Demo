pipeline {
  agent any
  stages {
    stage('package') {
      steps {
        sh 'mvn clean'
        sh 'mvn package'
      }
    }

    stage('deploy') {
      steps {
        sh 'mv target/demo-0.0.1-SNAPSHOT.jar /usr/local/src/'
      }
    }

  }
  tools {
    maven 'maven3.8.1'
  }
}