pipeline {
  agent none
  stages {
    stage('Build') {
      agent {
        docker {
          image 'schoolofdevops/node:4-alpine'
        }

      }
      steps {
        echo 'Building frontend ...'
        sh 'npm install'
      }
    }

    stage('Test') {
      agent {
        docker {
          image 'schoolofdevops/node:4-alpine'
        }

      }
      steps {
        echo 'Testing frontend ...'
        sh '''npm install
npm test'''
      }
    }

    stage('Package') {
      agent {
        docker {
          image 'schoolofdevops/node:4-alpine'
        }

      }
      steps {
        echo 'Packaging frontend ...'
        sh 'npm run package'
        archiveArtifacts(artifacts: '**/distribution/*.zip', fingerprint: true)
      }
    }

    stage('docker build and publish') {
      steps {
        script {
          docker.withRegistry('https://index.docker.io/v1/', 'dockerlogin') {
            def dockerImage = docker.build("vijiravichandran/frontend:v${env.BUILD_ID}", "./")
            dockerImage.push()
            dockerImage.push("latest")
          }
        }

      }
    }

  }
}