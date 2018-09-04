#!/usr/bin/env groovy

import hudson.FilePath
import jenkins.model.Jenkins

env.PROD='production'

node ('master') {
 if (env.PROD == "production") {

        try {
           stage('Production Release') {
           timeout(time: 2, unit: 'MINUTES') {
                 String shore_version = new File('/approot/jenkins/jobs/PAS_SHORE_PRO/pas.version').text
                 input message: 'Initiating Production release, Promote P@S Version : ' + shore_version +' to Shoreside Production, Shall we Proceed?',
                 ok: 'Proceed!'
                 }
           }


	try {

           stage('Shore Production') {
                String shore_prod = new File('/approot/jenkins/jobs/PAS_SHORE_PRO/pas.version').text
                echo 'Staring Shore side Production Release, P@S Version :' + shore_prod
                //build 'PAS_SHORE_PRO'
		sleep 5
                echo 'P@S Shore side Release bas been completed successfully with P@S Version :' + shore_prod
           }
	
	} catch(error) {
	  def user = error.getCauses()[0].getUser()
          }   

	try {
	stage('Shore Smoke Test') {
                echo 'Cheking Shore Production site status after deployment. '
                sh 'sh /approot/jenkins/jobs/PAS_DEV/workspace/PAS/ci/shell_scripts/bin/pax_intranet_smoke_test.sh https://princessatsea.cruises.princess.com/'
           }
	
	} catch(error) { // timeout reached or input false
           def user = error.getCauses()[0].getUser()
            if('SYSTEM' == user.toString()) { // SYSTEM means timeout.
                didTimeout = true
                echo "Sorry! No input was received before timeout"
          }
        }


	stage('Ship Version') {
		echo 'Checking Version'
		sleep 5
	}	  


    } catch(err) { // timeout reached or input false
           def user = err.getCauses()[0].getUser()
            if('SYSTEM' == user.toString()) { // SYSTEM means timeout.
                didTimeout = true
                echo "Sorry! No input was received before timeout"
          }
      }
  }
}
