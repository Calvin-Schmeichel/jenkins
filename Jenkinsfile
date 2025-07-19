pipeline {
  agent {
    docker {
      image 'jenkins/jenkins:lts'
      args '-u root -v /var/run/docker.sock:/var/run/docker.sock'
    }
  }
      
    stages {
        stage("Stage 1"){
            steps {
                echo "This is stage 1"
            }
        }
        stage("Stage 2"){
            steps {
                echo "This is stage 2"
            }
        }
        stage("Stage 3"){
            steps {
                echo "This is stage 3"
            }
        }
        stage("Stage 4"){
            steps {
                echo "This is stage 4"
            }
        }
        stage("Stage 5"){
            steps {
                echo "This is stage 5"
            }
        }
        stage('Deploy Python Container') {
            steps {
                script {
                    sh '''
                    apt-get update
                    apt-get install -y docker.io
                    docker pull python:3.12-slim
                    '''
                }
            }
        }
    }
}
