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
      def scannerHome = tool 'SonarScan4.8';
      withSonarQubeEnv('SonarQube') {
        sh "${scannerHome}/bin/sonar-scanner \
        -D sonar.login=admin \
        -D sonar.password=admin \
        -D sonar.projectKey=sonarqubetest \
        -D sonar.exclusions=vendor/**,resources/**,**/*.java \
        -D sonar.host.url=http://192.168.1XX.XX:9000/"
      }
    }

  }
  triggers {
    githubPush()
  }
}