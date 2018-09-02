#!/usr/bin/env groovy
import hudson.FilePath
import jenkins.model.Jenkins

node ('master') {

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


}

