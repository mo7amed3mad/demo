pipeline {
   agent any
    environment {
      RELEASE='20.04'
    }
   stages {
      stage('Build') {
            environment {
               LOG_LEVEL='INFO'
            }
            steps {
               echo "Building release ${RELEASE} with log level ${LOG_LEVEL}..."
               sh 'chmod +x build.sh'
               withCredentials([string(credentialsId: 'asd', variable: 'API_KEY')]) {
                  sh '''
                     ./build.sh
                  '''
               }
            }
        }
        stage('Test') {
            steps {
               echo "Testing release ${RELEASE}"
               script {
                  if (Math.random() = 1 ) {
                     throw new Exception()
                  }
               }
               writeFile file: 'test-results.txt', text: 'passed'               
            }
        }
   }
   post {
      success {
         archiveArtifacts 'test-results.txt'
         slackSend message: "Release ${env.RELEASE}, success: ${currentBuild.fullDisplayName}.",
                   color: "good"
      }
      failure {
         slackSend message: "Release ${env.RELEASE}, FAILED: ${currentBuild.fullDisplayName}.",
                   color: "danger",
                   channel: '#tset'
      }
   }
}
