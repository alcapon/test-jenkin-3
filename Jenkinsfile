pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/alcapon/test-jenkin-3', branch: 'main')
      }
    }

    stage('List Files') {
      steps {
        sh 'ls -la'
      }
    }

    stage('Current Dir') {
      steps {
        sh 'pwd'
      }
    }

    stage('SonarQubeScan') {
      steps {
        withSonarQubeEnv 'SonarScan'
      }
    }

  }
  triggers {
    githubPush()
  }
}