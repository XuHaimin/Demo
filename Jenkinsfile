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
        sh 'cd /usr/local/src/'
        sh 'setsid java -jar /usr/local/src/demo-0.0.1-SNAPSHOT.jar >/usr/local/src/demo.log 2>&1 &'
      }
    }

  }
  tools {
    maven 'maven3.8.1'
  }
}