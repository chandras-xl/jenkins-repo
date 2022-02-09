pipeline {
  agent any
  parameters{
    choice(name: 'PRODUCT',choices: ['RELEASE','DEPLOY'],description:'select the product')
    choice(name: 'PLATFORM',choices: ['EKS','AKS','ONPREM'],description: 'select the platform')
    choice(name: 'INSTALL',choices:['YES','NO'],description: 'Do you want to install the chart?')
  }
  options{
    timeout(time: 10,unit: 'MINUTES')
  }
  environment{
    RELEASE = '10.0'
  }
  stages{
    stage('Dependency'){
      steps{
        bat '''
          git --version
          aws --version
        '''
        installDependencies()
      }
      
    }
    stage('Selected choices'){
      steps{
        echo "Product: ${params.PRODUCT}"
        echo "PLATFORM: ${params.PLATFORM}"
        echo "INSTALL: ${params.INSTALL}"
      }
    }
    stage("Version"){
      steps {
        echo "Product version: ${env.RELEASE}"
      }  
    }
  }
  post{
    success{
      slackSend channel: '#jenkinsci',
                color: 'good',
                message: "Release ${env.RELEASE}, success: ${currentBuild.fullDisplayName}." 
    }
    failure{
      slackSend channel: '#jenkinsci',
                color: 'danger',
                message: "Release ${env.RELEASE}, failure: ${currentBuild.fullDisplayName}"
    }
  }
}

void installDependencies(){
  println("Installing dependencies")
}