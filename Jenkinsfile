pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh ' /home/mohan/Documents/Extracted_files/apache-maven-3.9.5/mvn install'
            }
        }
        stage('Deployment') {
            steps {
                sh 'cp target/grass02.war /home/mohan/Documents/Extracted_files/apache-tomcat-9.0.82/webapps ' 
            }
        }
    }
}

