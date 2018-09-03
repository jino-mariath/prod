#!/usr/bin/env groovy

node ('master') {

	def upStreamProjects = build.getParent().getUpstreamProjects()

	println "Found ${upStreamProjects.size()} upstream projects"

	upStreamProjects.each { p -> println "upstream project: ${p.getName()}" }

	//def upstream = currentBuild.rawBuild.getCause(hudson.model.Cause$UpstreamCause) 
        //def job = upstream?.shortDescription   
        //if(job != null) {                        
         //   println job

	   //stage ('Test') {
//		echo "Hello"
//	   }
 //} 
}
