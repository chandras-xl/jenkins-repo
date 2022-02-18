@Library('jenkins-shared-library@master') _

pipeline{
    agent any

    stages{
        stage('Git checkout'){
            steps{
                gitCheckout {
                    branch: "master",
                    url: "https://github.com/chandras-xl/jenkins-repo.git"
                }
            }
        }
    }
}
