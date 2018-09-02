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
     node {      
       def e2e = build job:'end-to-end-tests', propagate: false
       result = e2e.result
       if (result.equals("SUCCESS")) {
       } else {
          sh "exit 1" // this fails the stage
       }
     }
   }
} catch (e) {
   result = "FAIL" // make sure other exceptions are recorded as failure too
}

stage('deploy') {
   if (result.equals("SUCCESS")) {
      build 'deploy'
   } else {
      echo "Cannot deploy without successful build" // it is important to have a deploy stage even here for the current visualization
   }
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

