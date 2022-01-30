pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'npm install'
      }
    }

    stage('test') {
      environment {
        CI = 'true'
      }
      steps {
        sh 'sh ./jenkins/scripts/test.sh'
      }
    }

    stage('Deliver') {
      steps {
        sh 'sh ./jenkins/scripts/deliver.sh'
        input 'Finished using the web site? (Click "Proceed" to continue)'
        sh 'sh ./jenkins/scripts/kill.sh'
      }
    }

  }
}