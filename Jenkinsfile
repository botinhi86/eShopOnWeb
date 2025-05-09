pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'dotnet build eShopOnweb.sln'
      }
    }

    stage('Unit') {
      parallel {
        stage('Unit') {
          steps {
            sh 'dotnet test test/Unitests'
          }
        }

        stage('Integration') {
          steps {
            sh 'dotnet test test/IntegrationTests'
          }
        }

        stage('Functional') {
          steps {
            sh 'dotnet test test/Functionaltests'
          }
        }

      }
    }

    stage('Deployment') {
      steps {
        sh 'dotnet publish eShopOnweb.sln -o /var/aspnet'
      }
    }

  }
}