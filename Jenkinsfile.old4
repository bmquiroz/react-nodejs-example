pipeline {
  agent {
    // This image provides everything needed to run Cypress
    docker {
      image 'cypress/base:10'
      args '-u root:root'
    }
  }

  stages {
    // First stage installs node dependencies and Cypress binary
    stage('build') {
      steps {
        dir("my-app/") {
        // There a few default environment variables on Jenkins
        // on local Jenkins machine (assuming port 8080) see
        // http://localhost:8080/pipeline-syntax/globals#env
          echo "Running build ${env.BUILD_ID} on ${env.JENKINS_URL}"
          sh 'npm ci'
          // sh 'npm run cy:verify'
        }
      }
    }

    stage('start local server') {
      steps {
        // Start local server in the background
        // we will shut it down in "post" command block
          dir("my-app/") {
          sh 'nohup npm run start &'
        }
      }
    }
  }
}