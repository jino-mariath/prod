#!/usr/bin/env groovy

node ('master') {

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
