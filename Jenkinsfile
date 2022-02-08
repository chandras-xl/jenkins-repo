pipeline{
  agent any
  environment{
    RELEASE_VER = "1.0.0"
  }

  stages{
    stage("First stage"){
      environment{
        LOG_LEVEL = 'INFO'
      }
      steps{
        echo "This is stage 1"
        echo "The release version ${env.RELEASE_VER} and the log level is ${env.LOG_LEVEL}"
      }
    }
    stage("Second stage"){
      steps{
        echo "This is second stage"
        echo "The release version ${env.RELEASE_VER} and the log level is ${env.LOG_LEVEL}"
      }
    }
  }
}