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
                sh 'mvn -version'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'test -f target/devops-lab-1.0.0.jar'
                sh 'echo "JAR file created successfully"'
            }
        }

        stage('Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }
}
