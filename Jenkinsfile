pipeline {
    agent none
    stages {
        stage('git') {
            agent {label 'slave2'}
            steps {
                sh '''
                    if cd /home/ubuntu/jenkins/workspace/workspace/deployment/java_repo1;
                    then git pull;
                    else
                    git clone https://github.com/Kishoregt1302/java_repo1;
                    fi'''
            }
        }
       stage('build') {
           agent {label 'slave2'}
            steps {
                sh '''
                    if cd /home/ubuntu/jenkins/workspace/workspace/deployment/java_repo1;
                    then
					mvn clean install
					sleep 5
					cd target/
					chmod 666 *
					cp *.war /home/ubuntu/apache-tomcat-9.0.55/webapps
					else
					echo 'sdfasdf'
                    fi'''
					
            }
        }
    }
}
