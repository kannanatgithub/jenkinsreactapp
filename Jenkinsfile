pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
        echo 'Success'
      }
    }
    stage('Test') {
      steps {
        sh 'bash ./jenkins/scripts/test.sh'
        input(message: 'Is Test Success and ready to continue?', ok: 'Yes and Continue')
      }
    }
    stage('Deliver and Stop') {
      steps {
        sh 'bash ./jenkins/scripts/deliver.sh'
        input(message: 'Have u tested react app?', ok: 'Yes, continue to stop the server')
        sh 'bash ./jenkins/scripts/kill.sh'
      }
    }
  }
  environment {
    CI = 'true'
    HOME = '.'
    PORT_NUMBER = '9090'
  }
}