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
                sh '''echo "Deployed to  Dev"
elif  [ $ENV == "DEV" ];then
cp target/wcl.war /home/gaurav/Devops/apache-tomcat-9.0.89/webapps
echo "Deployed to  Qa"
elif  [ $ENV == "QA" ];then
cp target/wcl.war /home/gaurav/Devops/apache-tomcat-9.0.89/webapps
echo "Deployed to  Uat"
elif  [ $ENV == "UAT" ];then
cp target/wcl.war /home/gaurav/Devops/apache-tomcat-9.0.89/webapps
fi'''
            }
        }	

	}
        }		
