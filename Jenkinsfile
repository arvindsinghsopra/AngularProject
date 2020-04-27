pipeline {
  agent {
    node {
      label 'nodejs'
    }

  }
  stages {
    stage('Node Check') {
      steps {
        sh 'node -v'
      }
    }
    stage('NPM Check') {
      steps {
        sh 'npm -version'
      }
    }
    stage('Config Check') {
      steps {
        sh 'npm config get registry'
      }
    }
    stage('Install Dependencies') {
      steps {
        sh '''npm update
npm install'''
      }
    }
    stage('Build') {
      steps {
        sh 'npm run --ng build'
      }
    }
    stage('Test') {
      steps {
        CHROME_BIN=/usr/bin/google-chrome karma start --single-run
        sh 'npm run --ng test'
      }
    }
  }
}
