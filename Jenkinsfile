pipeline {
  agent any

  tools {
    maven 'maven'
  }

  stages {
    stage('Build') {
        steps {
            sh 'mvn clean package'
        }
    }

    stage('Test') {
 steps {
          echo 'TEst'
        }
    }

    stage('Code Quality') {
 steps {
          echo 'Quality'
        }
    }

    stage('Deploy to Dev') {
 steps {
          echo 'Dev'
        }
    }

    stage('Deploy to TEst') {
 steps {
          echo 'Test'
        }
    }

     stage('Deploy to UAT') {
 steps {
          echo 'UAT'
        }
    }

 stage('Deploy to Pre_rpd') {
 steps {
          echo 'Staging'
        }
    }

    stage('Deploy to Prod') {
 steps {
          echo 'Prod'
        }
    }
  }
}