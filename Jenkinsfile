pipeline{
  agent any
  environment{
    RELEASE_VER = "2.0"
  }
  stages{
    stage("Build"){
      environment{
        LOG_LEVEL = "INFO"
      }
      parallel{
        stage("linux-arm64"){
          steps{
            echo "Building release version ${env.RELEASE_VER} for ${env.STAGE_NAME} with log level of ${env.LOG_LEVEL}..."
          }
        }
        stage("linux-amd64"){
          steps{
            echo "Building release version ${env.RELEASE_VER} for ${env.STAGE_NAME} with log level of ${env.LOG_LEVEL}..."
          }
        }
        stage("windows-amd64"){
          steps{
            echo "Building release version ${env.RELEASE_VER} for ${env.STAGE_NAME} with log level of ${env.LOG_LEVEL}..."
          }
        }
      }
    }
    stage("Test"){
      steps{
        echo "Performing testing for product version ${env.RELEASE_VER}"
      }
    }
    stage("Deploy"){
      input{
        message 'Deploy?'
        ok 'Do it!'
        parameters{
          string(name: "ENVIRONMENT", defaultValue: "PROD", description: "Deploy to?")
        }
      }
      stage{
        steps{
          echo "Deploy version ${env.RELEAS_VER} onto ${ENVIRONMENT} environment"
        }
      }
    }
  }
  post{
    always{
      echo "I run always irrespective of success or failure"
    }
  }
}