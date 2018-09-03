#!/usr/bin/env groovy

node ('master') {

	def upstream = currentBuild.rawBuild.getCause(hudson.model.Cause$UpstreamCause) 
        def job = upstream?.shortDescription   
        if(job != null) {                        
            println job

	   stage ('Test') {
		echo "Hello"
	   }
 } 
}
