pipeline {
    agent { label 'JDK8-GOL'}
    options {
        timeout(time: 1, unit: 'HOURS')
    }
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('sourcecode') {
            steps {
                git url: 'https://github.com/Prasadsgithub/spring-petclinic.git', 
                branch: 'features'
            }   
        }
        stage('Build the code and sonarqube analysis') {
            steps {
                withSonarQubeEnv('SONAR_LATEST') {
                    sh 'mvn clean package sonar:sonar'
                }   
            }
        }  
        stage('reporting') {
            steps {
                junit testResults: '**/surefire-reports/*.xml'
            }
        }
    }
}