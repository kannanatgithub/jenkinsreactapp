pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'bash ./jenkins/scripts/test.sh'
        input(message: 'Is Test Success and ready to continue?', ok: 'Yes and Continue to Publish and Execute')
      }
    }
  }
  environment {
    CI = 'true'
    HOME = '.'
    PORT_NUMBER = '9090'
  }
}