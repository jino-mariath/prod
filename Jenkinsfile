#!/usr/bin/env groovy

<<<<<<< HEAD
=======
//import hudson.FilePath
//import jenkins.model.Jenkins

>>>>>>> de26d814ac0c3cd4b332158b9cafa12cbfd5d5c1
node ('master') {

        def upstream = currentBuild.rawBuild.getCause(hudson.model.Cause$UpstreamCause)
        def job = upstream?.shortDescription
        if(job == null) {
            println job
<<<<<<< HEAD
                env.PROD = 'production'
        }
}

node ('master') {
 if (env.PROD == "production") {

	try {
           stage('Production Release') {
           timeout(time: 2, unit: 'MINUTES') {
                 String shore_version = new File('/approot/jenkins/jobs/PAS_SHORE_GATE/pas.version').text
                 input message: 'Initiating Production release, Promote P@S Version : ' + shore_version +' to Shoreside Production, Shall we Proceed?',
                 ok: 'Proceed!'
                 }
              }

	   stage('Shore Production') {
		sh 'rsync -az /approot/jenkins/jobs/PAS_SHORE_GATE/pas.version /approot/jenkins/jobs//PAS_SHORE_PRO/'
		String shore_prod = new File('/var/lib/jenkins/jobs/PAS_SHORE_PRO/pas.version').text
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

  } else {


=======
		env.PROD = 'production'
	}
}

node ('master') {
 if (env.PROD == "production") {

	try {
                stage('Shoreside Production') {
                timeout(time: 2, unit: 'MINUTES') {
                        String shore_version = new File('/approot/jenkins/jobs/PAS_SHORE_PRO/pas.version').text
                        input message: 'Initiating Production release, Promote P@S Version : ' + shore_version +' to Shoreside Production, Shall we Proceed?',
                         ok: 'Proceed!'
                        }
                }
                stage('Test Ship Sites'){
                        echo 'Deploying P@S code to 17 Test ship instance. '
                        parallel (
                                PAS_RUBY: {
                                echo 'Starting RUBY'
                                def jobBuild = build(job: 'Test')
                        },

                                PAS_SUN: {
                        echo 'Copying P@S package to Dev Site'
                        echo 'Copying Deployment files...'
                        echo 'P@S code deployed to Dev site Successfully...'
                        sleep 10
                        }
                )
        }
        stage('Version') {
                echo 'Execuitng Version'
        }

        } catch(err) { // timeout reached or input false
            def user = err.getCauses()[0].getUser()
            if('SYSTEM' == user.toString()) { // SYSTEM means timeout.
                didTimeout = true
                echo "Sorry! No input was received before timeout"
        }

      }
 } else {
	
        try
           {
              stage ('Test')
              {
                 echo 'Lets Proceed'
                 sleep 10
              }

              stage ('Dev')
              {
                 echo 'Lets proceed to Dev site'
                 sleep 10
              }
             stage ('Build') {
                build 'Test'
                }

           }
         catch (error)
           {
           }
	}
}

>>>>>>> de26d814ac0c3cd4b332158b9cafa12cbfd5d5c1
