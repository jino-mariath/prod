#!/usr/bin/env groovy

node ('master') {
	def upstream = currentBuild.rawBuild.getCause(hudson.model.Cause$UpstreamCause) 
        def job = upstream?.shortDescription   
        if(job == null) {                        
            println job
		stage ('User') {
                wrap([$class: 'BuildUser']) {
                echo "userId=${BUILD_USER_ID},fullName=${BUILD_USER},email=${BUILD_USER_EMAIL}"
                def userId = env.BUILD_USER_ID
                def userName = env.BUILD_USER
                if((userId == "pc03069") || (userId == "pc05668") ||  (userId == "pc08300")) {
                        println ("Yes, Autherised User :" + userName)
	 try {
                stage('Shoreside Production') {
                timeout(time: 2, unit: 'MINUTES') {
                        String shore_version = new File('/approot/jenkins/jobs/PAS_SHORE_PRO/pas.version').text
                        input message: 'Initiating Production release, Promote P@S Version : ' + shore_version +' to Shoreside Production, Shall we Proceed?',
                         ok: 'Proceed!'
                        }
                }
        	stage('Exec Version') {
                	echo 'Execuitng Version'
   			currentBuild.result = 'SUCCESS'
			return
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
  }	
}
}
