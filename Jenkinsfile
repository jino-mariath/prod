#!/usr/bin/env groovy
import hudson.FilePath
import jenkins.model.Jenkins
import hudson.model.*

node ('master') {
	stage ('User') {
  		wrap([$class: 'BuildUser']) {
    		echo "userId=${BUILD_USER_ID},fullName=${BUILD_USER},email=${BUILD_USER_EMAIL}"
		def userId = env.BUILD_USER_ID
		def userName = env.BUILD_USER 
                        println ("Yes, Autherised User :" + userName)
			def upstream = currentBuild.rawBuild.getCause(hudson.model.Cause$UpstreamCause)
        		println upstream?.shortDescription


			def printCausesRecursively(cause) {
			     if (cause.class.toString().contains("UpstreamCause")) {
         			println "This job was caused by " + cause.toString()
         			for (upCause in cause.upstreamCauses) {
             				printCausesRecursively(upCause)
       				  }
     				} else {
         				println "Root cause : " + cause.toString()
				     }
			}


                }
	}
}
