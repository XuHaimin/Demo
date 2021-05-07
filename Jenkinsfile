pipeline {
  agent any
  stages {
    stage('package') {
      steps {
        sh 'mvn clean package'
      }
    }

    stage('deploy') {
      steps {
        sh 'mv target/demo.jar /usr/local/src/'
        withEnv(['JENKINS_NODE_COOKIE=dontkillme']){
                sh '''nohup java -jar /usr/local/src/demo.jar >/usr/local/src/demo.log 2>&1 &'''
        }
      }
    }

  }
  tools {
    maven 'maven3.8.1'
  }
  post {
    failure {
        echo '部署失败'
    }
    success {
        echo '部署成功'
    }
    unstable {
        echo '测试未通过'
    }
    always {
        echo '部署完成'
    }
  }
}