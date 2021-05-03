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
        sh '''OLD_BUILD_ID=$BUILD_ID
echo $OLD_BUILD_ID
export BUILD_ID=dontKillMe
nohup java -jar /usr/local/src/demo-0.0.1-SNAPSHOT.jar >demo.log 2>&1 &
export BUILD_ID=$OLD_BUILD_ID
echo $BUILD_ID'''
      }
    }

  }
  tools {
    maven 'maven3.8.1'
  }
}