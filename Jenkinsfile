pipeline {
    agent any
    triggers {
        pollSCM('H/1 * * * *')
    }
    stages {
        stage('Build') {
            steps {
                echo "Exécution de l'étape de build"
            }
        }
        stage('Hello1') {
            steps {
                sh 'echo hello1'
            }
        }
        stage('sleep') {
            steps {
                sh 'sleep 60'
            }
        }
        stage('Hello2') {
            steps {
                sh 'echo hello2'
            }
        }
    }
}