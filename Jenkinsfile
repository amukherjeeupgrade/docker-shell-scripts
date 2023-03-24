pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('darinpope-dockerhub')
  }
  stages {
    stage('Build') {
      steps {
        sh './Users/anindamukherjee/.jenkins/workspace/HeapDump_docker-shell_main/jenkins/build.sh'
      }
    }
    stage('Login') {
      steps {
        sh './Users/anindamukherjee/.jenkins/workspace/HeapDump_docker-shell_main/jenkins/login.sh'
      }
    }
    stage('Push') {
      steps {
        sh './Users/anindamukherjee/.jenkins/workspace/HeapDump_docker-shell_main/jenkins/push.sh'
      }
    }
  }
  post {
    always {
      sh './Users/anindamukherjee/.jenkins/workspace/HeapDump_docker-shell_main/jenkins/logout.sh'
    }
  }
}
