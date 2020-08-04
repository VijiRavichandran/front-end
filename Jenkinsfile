pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building frontend ...'
        sh 'npm install'
      }
    }
    stage('Test') {
      steps {
          echo 'Testing frontend ...'
          sh 'npm test'
      }
    }
    stage('Package') {
      steps {
        echo 'Packaging frontend ...'
        sh 'npm run package'
        archiveArtifacts artifacts: '**/distribution/*.zip', fingerprint: true
      }
    }
  }
}