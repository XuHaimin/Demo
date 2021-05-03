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
        sh '''export BUILD_ID=dontKillMe
nohup java -jar demo-0.0.1-SNAPSHOT.jar >demo.log 2>&1 &'''
      }
    }

  }
  tools {
    maven 'maven3.8.1'
  }
}