pipeline {
  agent any
  stages {
   stage ('Git Checkout') {
  steps {
      git branch: 'master', credentialsId: 'ranyaof', url: 'https://github.com/ranyaof/oOrders.git'
    }
  }

  }
}
