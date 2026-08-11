pipeline {
    agent any

    stages {
        stage('Checkout Info') {
            steps {
                sh 'whoami'
                sh 'hostname'
                sh 'pwd'
                sh 'git status'
            }
        }

        stage('System Info') {
            steps {
                sh 'cat /etc/os-release'
                sh 'java -version'
            }
        }
    }
}
