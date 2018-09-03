#!/usr/bin/env groovy

node ('master') {

	try
           {
	      println 'The Job Execues by: ' + job
	      echo ' Lets Start normal Execution'

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
