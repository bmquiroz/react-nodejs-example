pipeline {
  agent {
    // This image provides everything needed to run Cypress
    docker {
      image 'cypress/base:latest'
      args '-u root:root'
    }
  }

  stages {
    stage('build-and-test') {
    //   environment {
    //     // We will be recording test results and video on Cypress dashboard
    //     // to record we need to set an environment variable
    //     // we can load the record key variable from credentials store
    //     // see https://jenkins.io/doc/book/using/using-credentials/
    //     CYPRESS_RECORD_KEY = credentials('cypress-example-kitchensink-record-key')
    //   }

      steps {
        dir("my-app/") {
          sh 'npm ci'
          sh "npm run test:ci:record"
        }
      }
    }
  }
}