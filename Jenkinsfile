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
        writeFile file: "test-results.txt", text: "passed"
      }
    }
  }
    post{
      success{
        archiveArtifacts 'test-results.txt'
      }
    }
}