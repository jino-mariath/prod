#!/usr/bin/env groovy
import hudson.FilePath
import jenkins.model.Jenkins

//node ('master') {
//    try {
//        stage('Shoreside Production') {
//        timeout(time: 2, unit: 'MINUTES') {
//		String shore_version = new File('/approot/jenkins/jobs/PAS_SHORE_PRO/pas.version').text
//           	input message: 'Conformation : - Sall we deploy P@S code version :' + shore_version + ' to Shoreside production ?',
//            	ok: 'Proceed!'
//            }
//	}
//




def userInput = true
def didTimeout = false
try {
    timeout(time: 15, unit: 'SECONDS') { // change to a convenient timeout for you
        userInput = input(
        id: 'Proceed1', message: 'Was this successful?', parameters: [
        [$class: 'BooleanParameterDefinition', defaultValue: true, description: '', name: 'Please confirm you agree with this']
        ])
    }
} catch(err) { // timeout reached or input false
    def user = err.getCauses()[0].getUser()
    if('SYSTEM' == user.toString()) { // SYSTEM means timeout.
        didTimeout = true
    } else {
        userInput = false
        echo "Aborted by: [${user}]"
    }
}

node {
    if (didTimeout) {
        // do something on timeout
        echo "no input was received before timeout"
    } else if (userInput == true) {
        // do something
        echo "this was successful"
    } else {
        // do something else
        echo "this was not successful"
        currentBuild.result = 'FAILURE'
    } 
}





//    } catch(error) {
//        throw error
//    } finally {
//        
//    }
//   echo 'Execution Completed Successfully......!'
//}
