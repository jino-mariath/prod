#!/usr/bin/env groovy


env.DEV = 'development'
node ('master') {
	def upstream = currentBuild.rawBuild.getCause(hudson.model.Cause$UpstreamCause)
        def job = upstream?.shortDescription
        if(job == null) {
	env.DEV = 'development'
	}

  stage('plan') {
  	println $DEV
  }
  steps {
     sh 'ls -lah'
  }
}

