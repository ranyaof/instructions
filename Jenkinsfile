pipeline {
  agent any
  stages {
  
  stage('Checkout') {
    steps {
     git credentialsId: 'rany_github', url: 'https://github.com/ranyaof/oOrders.git', branch: 'master'
     }
  }
     stage('Restore packages'){
   steps{
      bat "dotnet restore Ftth.Api/Ftth.Api.csproj"
     }
  }
  stage('Clean'){
    steps{
        bat "dotnet clean Ftth.Api/Ftth.Api.csproj"
     }
   }
   stage('build packages'){
   steps{
      bat "dotnet build Ftth.Api/Ftth.Api.csproj  --configuration Release"
     }
  }

  stage('Publish'){
     steps{
       bat "dotnet publish Ftth.Api/Ftth.Api.csproj  -c Release"
   
     }
}


stage('Deliver for development') {
            when {
                branch 'development'
            }
            steps {
                sh './jenkins/scripts/deliver-for-development.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
        stage('Deploy for production') {
            when {
                branch 'production'
            }
            steps {
                sh './jenkins/scripts/deploy-for-production.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
  }
}
