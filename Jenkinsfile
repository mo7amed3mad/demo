pipeline {
  agent any
  stages {
    stage('stage1') {
      steps {
        echo '"this is $BUILD_NUMBER from $demo"'
        sh 'echo "this is $BUILD_NUMBER from $demo"'
      }
    }

  }
  environment {
    demo = '1'
  }
}