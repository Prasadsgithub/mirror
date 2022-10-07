node('JDK8') {
    stage('sourcecode') {
        git branch: 'features', url: 'https://github.com/Prasadsgithub/game-of-life.git'
    }
    stage('build the code') {
        sh 'mvn clean package'
    }
    stage('Archiving and test results') {
        junit '**/surefire-reports/*.xml'
    }
}
