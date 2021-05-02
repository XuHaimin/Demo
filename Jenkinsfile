pipeline {
  agent any
  stages {
    stage('package') {
      steps {
        sh '''mvn clean
'''
        sh 'mvn package'
      }
    }

  }
}