pipeline {
  agent any
  stages {
    stage('stage1') {
      steps {
        sh "echo this is $BUILD_NUMBER from $demo"
      }
    }

  }
  environment {
    demo = '1'
  }
}
