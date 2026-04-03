pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')
    }

    stages {

        stage('Clone') {
            steps {
                git branch: 'main',
                url: 'https://github.com/nivivarshna4/calculator-ci.git'
            }
        }

        stage('Compile') {
            steps {
                bat 'javac Calculator.java'
            }
        }

        stage('Run') {
            steps {
                bat 'java Calculator'
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: '*.class', fingerprint: true
        }
        failure {
            echo 'Build Failed'
        }
    }
}
