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
       // sh 'mv target/demo.jar /usr/local/src/'
       // withEnv(['JENKINS_NODE_COOKIE=dontkillme']){
       //         sh '''nohup java -jar /usr/local/src/demo.jar >/usr/local/src/demo.log 2>&1 &'''
       // }
       sh '''
                     STRING=`docker ps -a | grep test | awk '{print $1}'`
                     if [ -n "$STRING" ]; then
                         echo '删除镜像$STRING'
                         docker rm -f $STRING
                     fi
                     '''
        sh '''
                         STRING=`docker images | grep test | awk '{print $1}'`
                         if [ -n "$STRING" ]; then
                            echo '停止容器$STRING'
                            docker stop $STRING
                            echo '删除容器$STRING'
                            docker rm $STRING
                         fi
                      '''
       echo '构建镜像'
       sh 'docker build -t test:v1 .'
       echo '启动容器'
       sh 'docker run -itd -p 9090:9090 --name test test:v1'
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