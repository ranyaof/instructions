pipeline {
  agent any
  stages {
   stage ('Git Checkout') {
  steps {
      git clone: 'master', credentialsId: 'rany_github', url: 'https://github.com/ranyaof/oOrders.git'
    }
  }

  }
}
