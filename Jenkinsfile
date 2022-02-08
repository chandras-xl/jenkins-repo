pipeline {
  agent any
  environment{
    RELEASE = "2.0"
  }
  stages{
    environment{
      LOG_LEVEL = "INFO"
    }
    stage("Build"){
      steps{
        echo "The is a build stage"
        echo "The build number ${env.BUILD_ID} build version ${env.RELEASE} and log leve ${env.LOG_LEVEL}"
      }
    }
    stage("Test"){
      steps{
        echo "This is testing phase"
      }
    }
    stage("Deploy"){
      input {
        message 'Deploy?'
        ok "Do it!"
        parameters{
          string(name: "TARGET_ENV", defaultValue: "DEV", description: "Target deployment environment")
        }
      }
      steps{
        echo "Deploying the release ${env.RELEASE} on ${TARGET_ENV}"
      }
    }
  }
  post{
    always{
      echo "I always execute irrespective of success or failure"
    }
  }
}