#!/usr/bin/env groovy

node ('master') {

	def upstream = currentBuild.rawBuild.getCause(hudson.model.Cause$UpstreamCause) 
        def job = upstream?.shortDescription   
        if(job.trim() != null) {                        
            println job
 } 
}
