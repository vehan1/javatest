pipeline {
  agent any

  tools {
    maven 'maven'
  }

  environment {
    AWS_SECRET_KEY='test'
  }

  stages {
    stage('Build') {
        steps {
            sh 'mvn clean package'
        }
    }

    stage('Test') {
 steps {
          echo '$AWS_SECRET_KEY'
        }
    }

    stage('Input') {
            steps {
                if (env.BRANCH_NAME == 'feature/test') {
                input('Do you want to proceed?')

  }
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

        post {
    failure {
        mail to: 'team@example.com',
             subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
             body: "Something is wrong with ${env.BUILD_URL}"
    }
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

 stage('Deploy to Pre_prod') {
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