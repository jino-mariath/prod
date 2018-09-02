#!/usr/bin/env groovy
import hudson.FilePath
import jenkins.model.Jenkins

node ('master') {
    try {
        stage('Shoreside Production') {
        timeout(time: 2, unit: 'MINUTES') {
		String shore_version = new File('/approot/jenkins/jobs/PAS_SHORE_PRO/pas.version').text
           	input message: 'Initiating Production release, Promote P@S Version : ' + shore_version +' to Shoreside Production, Shall we Proceed?',
            	ok: 'Proceed!'
	        }
	    }

	try {
	   stage('end-to-end-tests') {
       		echo 'Execution ........'
		ls- la
       	   }
	} catch (e) {
   		result = "FAIL" // make sure other exceptions are recorded as failure too
	}

	try { 
	  stage('deploy') {
   	  echo '2nd Execution'
	  sh 'ls- la'
	  }
	} catch (e) {
	}	

	} catch(err) { // timeout reached or input false
	    def user = err.getCauses()[0].getUser()
	    if('SYSTEM' == user.toString()) { // SYSTEM means timeout.
        	didTimeout = true
		echo "Sorry! No input was received before timeout" 
	    } else {
        	userInput = false
	        echo "Aborted by: [${user}]"
    	    }
	}
}

