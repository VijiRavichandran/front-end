pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building frontend ...'
        sh 'nvm install'
      }
    }
    stage('Test') {
      steps {
          echo 'Testing frontend ...'
          sh 'nvm test'
      }
    }
    stage('Package') {
      steps {
        echo 'Packaging frontend ...'
        sh 'nvm run package'
        archiveArtifacts artifacts: '**/distribution/*.zip', fingerprint: true
      }
    }
  }
}