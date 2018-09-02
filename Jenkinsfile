#!/usr/bin/env groovy
import hudson.FilePath
import jenkins.model.Jenkins

node ('master') {

	stage ('User') {
  		wrap([$class: 'BuildUser']) {
    		echo "userId=${BUILD_USER_ID},fullName=${BUILD_USER},email=${BUILD_USER_EMAIL}"
		def user = env.BUILD_USER_ID 
		if(user == "pc08300") {
                        println ("Yes, User is :" + user)
                        } else {
                        println ("Sorry, User is - : " + ${BUILD_USER_ID})
                        }
                }
	}
}

