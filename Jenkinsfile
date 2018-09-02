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
                }
	}
}
