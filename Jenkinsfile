pipeline {
	agent any 
	
	parameters {
  		string defaultValue: 'QA', name: 'ENV'
	}
	
	triggers {
  		pollSCM '* * * * *'
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
			script {
			 if ( env.ENV == 'QA' ){
        	sh 'cp target/PIPELINE.war /home/swapnil/Documents/DevOps-Software/apache-tomcat-9.0.79/webapps'
        	echo "deployment has been COMPLETED on QA!"
			 }
			else ( env.ENV == 'UAT' ){
    		sh 'cp target/PIPELINE.war /home/swapnil/Documents/DevOps-Software/apache-tomcat-9.0.79/webapps'
    		echo "deployment has been done on UAT!"
			}
			}}}
		stage('slack-notification'){
		   steps {
		     slackSend baseUrl: 'https://hooks.slack.com/services/', channel: '#april-fool', color: 'good', message: 'Welcome to Jenkins SLACK NOTIFICATION', teamDomain: 'devops', tokenCredentialId: 'april'
		     }}
}}
