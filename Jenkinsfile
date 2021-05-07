pipeline {
  agent any
  stages {
    stage('package') {
      steps {
        tool name: 'maven3.8.1', type: 'maven'
        sh 'mvn clean package'
      }
    }

    stage('deploy') {
      steps {
        sh 'mv target/demo-0.0.1-SNAPSHOT.jar /usr/local/src/'
        dir('/usr/local/src/'){
            withEnv(['JENKINS_NODE_COOKIE=dontkillme']){
                sh '''nohup java -jar /usr/local/src/demo-0.0.1-SNAPSHOT.jar >/usr/local/src/demo.log 2>&1 &'''
            }
        }
      }
    }
  }
}