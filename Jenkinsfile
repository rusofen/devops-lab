pipeline {
    agent { label 'linux' }

    stages {

        stage('Compile') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
    steps {
        sh 'mvn test'
    }

    post {
        always {
            junit 'target/surefire-reports/*.xml'
        }
    }
}

        stage('Package') {
            steps {
                sh 'mvn package -DskipTests'
            }
        }

        stage('Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }

    }
}
