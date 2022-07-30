pipeline {
  agent any 

  tools {
    maven 'mvn'
  }

  environment {
        DISABLE_AUTH = 'true'
  }

  stages {
    stage('Build') {
      agent {
        label 'java'
      }
      steps {
        echo 'Build ' + env.BRANCH_NAME
        sh 'mvn clean install'
      }
    }

    stage('Scanning') {
      steps {
        echo "${DISABLE_AUTH}"
        echo 'Scanning'
      }
    }
  }

}