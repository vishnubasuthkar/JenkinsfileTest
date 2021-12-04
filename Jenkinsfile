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
                    git clone https://github.com/vishnubasuthkar/java_repo1;
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
					else
					echo 'sdfasdf'
                    fi'''
					
            }
        }
        stage('deploy') {
           agent {label 'slave2'}
            steps {
                sh '''
					cd /home/ubuntu/jenkins/workspace/workspace/deployment/java_repo1/target/
					sudo chmod 666 *
					cp *.war /home/ubuntu/apache-tomcat-9.0.55/webapps
					echo 'finished'
                    '''
					
            }
        }
    }
}
