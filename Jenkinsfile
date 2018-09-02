#!/usr/bin/env groovy
import hudson.FilePath
import jenkins.model.Jenkins

	stage ('User') {
  		wrap([$class: 'BuildUser']) {
    		echo "userId=${BUILD_USER_ID},fullName=${BUILD_USER},email=${BUILD_USER_EMAIL}"
		def userId = env.BUILD_USER_ID
		def userName = env.BUILD_USER 
		if((userId == "pc03069") || (userId == "pc05668") ||  (userId == "pc08300")) {
                        println ("Yes, Autherised User :" + userName)
                        } else {
                        
			println ("Sorry, User is - : " + ${BUILD_USER_ID})
                        }
                }
	}

