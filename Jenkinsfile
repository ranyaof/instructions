pipeline {
  agent any
  stages {
  
  stage('Checkout') {
    steps {
     git credentialsId: 'rany_github', url: 'https://github.com/ranyaof/oOrders.git', branch: 'master'
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

  }
}
