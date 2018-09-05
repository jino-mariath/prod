#!/usr/bin/env groovy
import hudson.FilePath
import jenkins.model.Jenkins

env.SCRIPT_DIR = '/approot/jenkins/jobs/PAS_DEV/workspace/PAS/scripts'
env.JOB_DIR = '/approot/jenkins/jobs'

def shoreProduction() {

	stage ('Shore Production') {
		sh 'rsync -az $JOB_DIR/PAS_SHORE_GATE/pas.version $JOB_DIR/PAS_SHORE_PRO/'
		String shore_prod = new File('/approot/jenkins/jobs/PAS_SHORE_PRO/pas.version').text
		echo 'Staring Shore side Production Release, P@S Version :' + shore_prod
		build 'PAS_SHORE_PRO'
		echo 'P@S Shore side Release bas been completed successfully with P@S Version :' + shore_prod
	}

	stage ('Shore Smoke Test') {
		echo 'Cheking Shore Production site status after deployment. '
		sh 'sh $JOB_DIR/PAS_DEV/workspace/PAS/ci/shell_scripts/bin/pax_intranet_smoke_test.sh https://princessatsea.cruises.princess.com/'
        }

	stage ('Shore Lab & Acquia Deployment') {
		String shore_prod = new File('/approot/jenkins/jobs/PAS_SHORE_PRO/pas.version').text
		echo 'Deploying P@S Version : ' + shore_prod +' to Ship Labs, Acquia and Ship Clone sites '
		
		parallel ('P@S Acquia': {
			build(job: 'PAS_ACQUIA_DB', wait:false)
			},

			PAS_SHIP_LAB: {
			build(job: 'PAS_SHIPLAB', wait:false)
			},

			PAS_SHIP_CLONE: {
			build(job: 'PAS_SHIP_CLONE', wait:false)
			}
		)
	}
}



node ('master') {

        def upstream = currentBuild.rawBuild.getCause(hudson.model.Cause$UpstreamCause)
        def job = upstream?.shortDescription
        if(job == null) {
            println job
                env.PROD = 'production'
        }
}

node ('master') {
 if (env.PROD == "production") {
   try {
	stage ('Production Release') {
           timeout(time: 2, unit: 'MINUTES') {
                 String shore_version = new File('/approot/jenkins/jobs/PAS_SHORE_GATE/pas.version').text
                 input message: 'Initiating Production release, Promote P@S Version : ' + shore_version +' to Shoreside Production, Shall we Proceed?',
                 ok: 'Proceed!'
                 }
              }
	shoreProduction()

		
sh / ----- => Ship Release <= ----

   try {
	   stage ('Ship Release') {
		String shore_prod = new File('/approot/jenkins/jobs/PAS_SHORE_PRO/pas.version').text
		echo 'Starting Passenger Ship Release P@S Version :' + shore_prod
	   
		parallel ('CARIBBEAN': {
			build 'PAS_CARIBBEAN'
			},
	
			CORAL: {
			build 'PAS_CORAL'
			},
			
			CROWN: {
			build 'PAS_CROWN'
			},

			DIAMOND: {
			build 'PAS_DIAMOND'
			},

			EMERALD: {
			build 'PAS_EMERALD'
			},

			GOLDEN: {
			build 'PAS_GOLDEN'
			},

			GRAND: {
			build 'PAS_GRAND'
			},

			ISLAND: {
			build 'PAS_ISLAND'
			},
			
			MAJESTIC: {
			build 'PAS_MAJESTIC'
			},

			PACIFIC: {
			build 'PAS_PACIFIC'
			},

			REGAL: {
			build 'PAS_REGAL'
			},
		
			ROYAL: {
			build 'PAS_ROYAL'
			},

			RUBY: {
			build 'PAS_RUBY'
			},

			SAPPHIRE: {
			build 'PAS_SAPPHIRE'
			},

			SEA: {
			build 'PAS_SEA'
			},

			STAR: {
			build 'PAS_STAR'
			},

			SUN: {
			build 'PAS_SUN'
			}
			
		)

	   }

	} catch(error) {

	}

	stage ('P@S Ship Version') {
		echo 'Checking all 17 ship lateste P@S release version.'
		build 'PAS_SHIP_VERSION'
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

