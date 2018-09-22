// Powered by Infostretch 

pipeline {
	tools {
		maven 'Maven 3.3.9'
        jdk 'jdk8'
	}

node () {

	stage ('test-convertBuild - Checkout') {
 	 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '982803f5-175d-4a52-b0c5-faefd8cd79e6', url: 'https://github.com/nsalin/jenkinstest.git']]]) 
	}
	stage ('test-convertBuild - Build') {
 	
// Unable to convert a build step referring to "hudson.plugins.timestamper.TimestamperBuildWrapper". Please verify and convert manually if required.		// Maven build step
	steps { 
 			if(isUnix()) {
 				sh "mvn clean test " 
			} else { 
 				bat "mvn clean test " 
			} 
 		} 
	}
	stage ('test-convertBuild - Post build actions') {
/*
Please note this is a direct conversion of post-build actions. 
It may not necessarily work/behave in the same way as post-build actions work.
A logic review is suggested.
*/
		// Mailer notification
		step([$class: 'Mailer', notifyEveryUnstableBuild: true, recipients: 'stelian.alin@yahoo.com', sendToIndividuals: false])
 
	}
}
}
