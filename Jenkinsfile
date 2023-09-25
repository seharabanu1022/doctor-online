pipeline{
    agent any
    parameters {
  choice choices: ['dev', 'test', 'prod'], description: 'deploy application to desired environment', name: 'envName'
}
  stages{
        stage("maven build"){
            steps{
                sh "mvn clean package"
            }
        }
      stage("deploy to dev"){
          when{
              expression { params.envName=="dev" }
          }
          steps{
              echo "deploy to dev"
            }
        }
      stage("deploy to test"){
          steps{
              echo "deploy to test"
    }
}
