#!/usr/bin/env groovy
import hudson.FilePath
import jenkins.model.Jenkins

node ('master') {

	stage ('User') {
		
		node {
  		wrap([$class: 'BuildUser']) {
    		def user = env.BUILD_USER_ID
  		}
		}

	}

}

