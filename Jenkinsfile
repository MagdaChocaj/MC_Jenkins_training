pipeline {
    agent {label "slave01-new"}
    options {
        buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '7', numToKeepStr: '3')
        timeout(5)
        timestamps()
      }
      environment {
        env01 = "production"
        env02 = "test"
      }
      stages {
        stage('Show environments') {
            steps {
                echo "Environment: $env01"
                echo "Environment: $env02"
            }
        }
        stage('Timeout ovveride') {
            options {
              timeout(time: 30, unit: 'SECONDS')
            }
            steps {
                sleep 60
            }
        }
    }
    post {
      always {
        cleanWs()
      }
    }
}
