pipeline {
    agent any
           triggers {
  pollSCM ' * * * * *'
		    }
	parameters {
  choice choices: ['DEV', 'QA', 'UAT'], name: 'ENV'
		}
 
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh '/home/gaurav/Devops/apache-maven-3.9.6/bin/mvn install'
            }
        }
        stage('Deployment') {
            steps {
                sh '''if [$ENV == \'DEV\'];then
cp target/wcl.war /home/gaurav/Devops/apache-tomcat-9.0.89/webapps
if [$ENV == \'QA\'];then
cp target/wcl.war /home/gaurav/Devops/apache-tomcat-9.0.89/webapps
if [$ENV == \'UAT\'];then
cp target/wcl.war /home/gaurav/Devops/apache-tomcat-9.0.89/webapps
fi'''
            }
        }	

	}
        }		
