#!/usr/bin/env groovy

import hudson.FilePath
import jenkins.model.Jenkins

node ('master') {

	try {
           stage('Production Release') {
           timeout(time: 2, unit: 'MINUTES') {
                 String shore_version = new File('/approot/jenkins/jobs/PAS_SHORE_PRO/pas.version').text
                 input message: 'Initiating Production release, Promote P@S Version : ' + shore_version +' to Shoreside Production, Shall we Proceed?',
                 ok: 'Proceed!'
                 }
              }

	   stage('Shore Production') {
		String shore_prod = new File('/approot/jenkins/jobs/PAS_SHORE_PRO/pas.version').text
		echo 'Staring Shore side Production Release, P@S Version :' + shore_prod
		//build 'PAS_SHORE_PRO'
		sleep 5
		echo 'P@S Shore side Release completed successfully with P@S Version :' + shore_prod
	   }
	   stage('Shore SmokeTest') {
		echo "Smoketest"
		sleep 2
	   }


	   stage('Ship Production') {
		echo 'Executing Ship Release .....'
		sleep 2
		build 'SHIP_PRO'
	   }
 

    } catch(err) { // timeout reached or input false
            def user = err.getCauses()[0].getUser()
            if('SYSTEM' == user.toString()) { // SYSTEM means timeout.
                didTimeout = true
                echo "Sorry! No input was received before timeout"
        }
      }
}
