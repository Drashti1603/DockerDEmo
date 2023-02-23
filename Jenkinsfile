

pipeline {
    agent any
    environment {
        NEW_VERSION = '1.3.0'
        SERVER_CREDENTIALS = credentials('server')
    }
    stages {
        stage('build') {
            
            steps {
                echo 'building the application'
                echo "Software version is ${NEW_VERSION}"
            }
        }
      stage('test') {
          when{
              expression{
                  env.BRANCH_NAME == 'dev'
              }
          }
            steps {
                echo 'testing the application'
            }
        }
      stage('deploy') {
            steps {
                echo 'deplying the application'
                // sh 'wrong command'
                sh "${SERVER_CREDENTIALS}"
            }
        }
    }
    post{
        always{
            echo 'Executing always'
        }
        success{
            echo 'Executing success'
        }
        failure{
            echo 'Executing failure'
        }
    }
}
