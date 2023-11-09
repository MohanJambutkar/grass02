pipeline {
    agent any

parameters {
  choice choices: ['TEST', 'STAGE', 'DEV', 'QA', 'PROD'], name: 'ENV'
}

triggers {
        pollSCM('*/1 * * * *') // This sets up polling SCM to check for changes every minute
    }

    stages {
        stage('checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh ' /home/mohan/Documents/Extracted_files/apache-maven-3.9.5/bin/mvn install'
            }
        }
        stage('Deployment') {
            steps {
                sh 'cp target/grass02.war /home/mohan/Documents/Extracted_files/apache-tomcat-9.0.82/webapps ' 
            }
        }
        stage('slack notification') {
            steps {
                slackSend baseUrl: 'https://hooks.slack.com/services/', botUser: true, channel: '# test', color: 'good ', message: 'env dev ', notifyCommitters: true, teamDomain: 'Dev', tokenCredentialId: 'testtocken02'
         }
        }
    }
}

