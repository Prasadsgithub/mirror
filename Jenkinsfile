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
                git url: 'https://github.com/Prasadsgithub/game-of-life.git', 
                branch: 'features'
            }    
        }
        stage('Build the code and sonarqube analysis') {
            steps {
                withSonarQubeEnv(SONAR_LATEST') {
                    'sh script: 'mvn package'
                }

                // stash name: 'gameoflife-build' , includes: 'target/*.jar'
            }
        }   
        stage('reporting') {
            steps {
                junit testResults: 'target/surefire-reports/*.xml'
            }
        }
    }
    }