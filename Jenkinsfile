#!/usr/bin/env groovy
import hudson.FilePath
import jenkins.model.Jenkins

node ('master') {
    try {
        stage('Shoreside Production') {
        timeout(time: 2, unit: 'MINUTES') {
		String shore_version = new File('/approot/jenkins/jobs/PAS_SHORE_PRO/pas.version').text
            	input message: 'Shall we deploy P@S code' + shore_version + ' to Shoreside production ?',
            	ok: 'Proceed!'
            }
	}

    } catch(error) {
        throw error
    } finally {
        
    }
   echo 'Execution Completed Successfully......!'
}
