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
    stage('Print Configured Branch') {
      steps {
        script {
          def branch = env.GIT_BRANCH?.replaceFirst(/^origin\//, '')
    
          def isMain = branch == "main"
          def isDev  = branch?.endsWith("-dev")
          def isQa   = branch?.endsWith("-qa")
    
          echo "Branch: ${branch}"
          echo "Is main: ${isMain}"
          echo "Ends with -dev: ${isDev}"
          echo "Ends with -qa: ${isQa}"

          if (isMain) {
            echo "Production deployment logic"
          } else if (isQa) {
            echo "QA deployment logic"
          } else if (isDev) {
            echo "Dev deployment logic"
            env.TEST_SECRET = credentials('DEV_TEST_SECRET')
            sh 'TEST_SECRET=$DEV_TEST_SECRET'
          }
        }
      }
    }
  }
}
