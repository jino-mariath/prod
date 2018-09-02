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
			
def currentBuild = Thread.currentThread().executable

def job = hudson.model.Hudson.instance.getJob("PAS_DEV")
def cause = new hudson.model.Cause.UpstreamCause(currentBuild)
def causeAction = new hudson.model.CauseAction(cause) 
			println currentBuild
			println job
			println cause
			println causeAction
                }
	}
}
