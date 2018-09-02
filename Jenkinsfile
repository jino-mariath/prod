#!/usr/bin/env groovy
import hudson.FilePath
import jenkins.model.Jenkins

node ('master') {

	stage ('User') {
  		wrap([$class: 'BuildUser']) {
    		echo "userId=${BUILD_USER_ID},fullName=${BUILD_USER},email=${BUILD_USER_EMAIL}"
		if(${BUILD_USER_ID} == "pc08300") {
                        println ("Yes, User is :" + userId)
                        } else {
                        println ("Sorry, User is - : " + ${BUILD_USER_ID})
                        }
                }
	}
}

