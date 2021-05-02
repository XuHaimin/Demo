pipeline {
  agent any
  stages {
    stage('tools') {
      steps {
        sh 'echo Init'
        tool(name: 'maven3.8.1', type: 'maven')
      }
    }

    stage('package') {
      steps {
        sh 'mvn clean'
        sh 'mvn package'
      }
    }

  }
}