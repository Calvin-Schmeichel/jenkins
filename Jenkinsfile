pipeline {
  agent any

  stages {
    stage("Stage 1") {
      steps {
        echo "This is stage 1"
      }
    }
    stage("Stage 2") {
      steps {
        echo "This is stage 2"
      }
    }
    stage("Stage 3") {
      steps {
        echo "This is stage 3"
      }
    }
    stage("Stage 4") {
      steps {
        echo "This is stage 4"
      }
    }
    stage("Stage 5") {
      steps {
        echo "This is stage 5"
      }
    }
    stage('Deploy Python Container') {
      steps {
        sh '''
          docker pull python:3.12-slim
          docker rm -f my-python-container || true
          docker run -d --name my-python-container python:3.12-slim sleep infinity
        '''
      }
    }
  }
}
