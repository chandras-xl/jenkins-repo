pipeline {
  agent any
  stages {
    stage('stage1') {
      steps {
        echo "The Build number is $BUILD_ID and the value of env DEMO is $DEMO"
      }
    }

  }
  environment {
    DATA = '100'
  }
}
