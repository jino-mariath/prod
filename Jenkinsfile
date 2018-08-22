#!/usr/bin/env groovy
import hudson.FilePath
import jenkins.model.Jenkins

node ('master') {
    try {
        stage('Shoreside Production') {
        timeout(time: 2, unit: 'MINUTES') {
            input message: 'Please confirm can we deploy P@S code to Shoreside production ?',
            ok: 'Fire!'
            }
	}

    } catch(error) {
        throw error
    } finally {
        
    }
   echo 'Execution Completed Successfully......!'
}
