#!/usr/bin/env groovy

node ('master') {
 env.DEV="deployment"

stage('plan') {
  when {
     environment name: 'DEV', value: 'deployment'
  }
  steps {
     sh 'ls -lah'
  }
}

}

