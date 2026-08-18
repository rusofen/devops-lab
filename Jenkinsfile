pipeline {
    agent { label 'linux' }

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

        stage('Build') {
            steps {
                sh 'mkdir -p dist'
                sh 'echo "DevOps Lab Build" > dist/app.txt'
                sh 'cat dist/app.txt'
            }
        }
        stage('Test') {
    steps {
        sh 'test -f dist/app.txt'
        sh 'grep -q "DevOps Lab Build" dist/app.txt'
        sh 'echo "Tests passed"'
        }
    }
        stage('Artifact') {
    steps {
        archiveArtifacts artifacts: 'dist/app.txt', fingerprint: true
    }
}
}
}
