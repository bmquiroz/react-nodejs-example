pipeline {
  agent {
    // This image provides everything needed to run Cypress
    label 'docker-build-agent'
  }
  stages {
    stage('checkout-branch') {
      steps {
        checkout scm
      }
    }
    stage('build-and-test') {
      agent {
        docker {
          // image 'cypress/base:latest'
          image 'node:16.13.1-alpine'
          reuseNode true
        }
      }
    //   environment {
    //     // We will be recording test results and video on Cypress dashboard
    //     // to record we need to set an environment variable
    //     // we can load the record key variable from credentials store
    //     // see https://jenkins.io/doc/book/using/using-credentials/
    //     CYPRESS_RECORD_KEY = credentials('cypress-example-kitchensink-record-key')
    //   }

      steps {
        dir("my-app/") {
          sh 'pwd'
          sh 'npm ci'
          sh "npm run test:ci:record"
        }
      }
    }
  }
}