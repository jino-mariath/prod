#!/usr/bin/env groovy

node ('master') {

	def upstream = currentBuild.rawBuild.getCause(hudson.model.Cause$UpstreamCause) 
        def job = upstream?.shortDescription   
        if(job != null) {                        
           println job

	stage('Parent') {
	  options {
	    lock('master')
  	}
  	stages {
    		stage('one') {
		echo 'hello stage 1'
    		}
   		 stage('two') {
		 echo 'Stage 2'
    }
  }
}
}
}
