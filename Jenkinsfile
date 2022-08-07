pipeline {
  agent {
    label 'java'
  }

  tools {
    maven 'maven1'
  }

  stages {
    stage('Build') {
        steps {
            sh 'mvn clean package'
        }
    }

    stage('Test') {
      steps {
          echo "${env.BUILD_NUMBER}"
          echo "${env.BUILD_URL}"
        }
    }


    stage('Code Quality') {
      steps {
          echo 'Code Quality'
        }
    }

    stage('Deploy to Dev') {
      steps {
          echo 'Dev'
        }
    }

    stage('Deploy to Test') {
      steps {
          echo 'Test'
        }
    }
    stage('Run Tests') {
            parallel {
                stage('Test On Windows') {
                    agent 
                        echo "windows"
                    
                    steps {
                        bat "run-tests.bat"
                    }
                    post {
                        always {
                            junit "**/TEST-*.xml"
                        }
                    }
                }
                stage('Test On Linux') {
                    agent 
                        echo "linux"
                    
                    steps {
                        sh "run-tests.sh"
                    }
                    post {
                        always {
                            junit "**/TEST-*.xml"
                        }
                    }
                }
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

    stage('Prod Approval') {
      steps {
        script {
          if (env.BRANCH_NAME == "master") {
            input('Proceed for Prod Deployment ?')
          }
        }
      }
    }

    stage('Deploy to Prod') {
      when { branch 'master'}
      steps { 
          echo 'Prod'         
        }

        post {
          failure {
            echo 'Sending Notification'
          }
        }
    }
  }

   post {
        always {
            echo 'I have finished'
        }
        success {
            echo 'I succeeded!'
        }
        unstable {
            echo 'I am unstable'
        }
        failure {
             mail to: 'team@example.com',
             subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
             body: "Something is wrong with ${env.BUILD_NUMBER}"
        }
        changed {
            echo 'Things were different before'
        }
    }
}
