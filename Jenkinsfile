pipeline {
	agent any 
	
	parameters {
  		choice choices: ['DEV', 'QA', 'UAT'], name: 'ENV'
	}
	stages {
	    stage('Checkout') {
	        steps {
			checkout scm			       
		      }}
		stage('Build') {
	           steps {
			  sh '/home/swapnil/Documents/DevOps-Software/apache-maven-3.9.4/bin/mvn install'
	                 }}
		stage('Deployment'){
		   steps {
		   	Script {
		   if [ $ENV = "QA" ];then
        		sh 'cp target/CICD.war /home/swapnil/Documents/DevOps-Software/apache-tomcat-9.0.79/webapps'
		   elif  [ $ENV = "UAT" ];then
		   	sh 'cp target/PIPELINE.war /home/swapnil/Documents/DevOps-Software/apache-tomcat-9.0.79/webapps'
         	echo "deployment has been done!"
		   fi
			}}}	
}}
