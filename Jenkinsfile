pipeline{
  agent any
  environment{
    RELEASE = "10.0"
  }
  stages{
    stage("Build"){
      environment{
        LOG_LEVEL = "INFO"
      }
      steps{
        echo "Building version ${env.RELEASE} with log ${env.LOG_LEVEL}"
      }
    }
    stage("Test"){
      steps{
        echo "Testing the release ${env.RELEASE}"
        script {
          if (Math.random() > 1 ){
              throw new Exception()
          }
        }
        writeFile file: "test-results.txt", text: "passed"
      }
    }
  }
    post{
      success{
        archiveArtifacts 'test-results.txt'
        slackSend channel: '#jenkinsci',
                  color: 'good',
                  message: "Release ${env.RELEASE}, success: ${currentBuild.fullDisplayName}."
      }
      failure{
        slackSend channel: '#jenkinci',
                  color: 'danger',
                  message: "Release ${env.RELEASE}, failure: ${currentBuild.fullDisplayName}."
      }
    }
}