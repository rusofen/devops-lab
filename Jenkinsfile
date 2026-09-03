pipeline {
    agent { label 'linux' }

    environment {
        APP_NAME = 'devops-lab'
        APP_VERSION = '1.0.0'
    }

    stages {

        stage('Compile') {
            steps {
                sh 'echo "Application: $APP_NAME"'
                sh 'echo "Version: $APP_VERSION"'
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

    post {
        always {
            echo 'Pipeline finished'
        }

        success {
            echo 'Pipeline SUCCESS'
        }

        failure {
            echo 'Pipeline FAILED'
        }

        unstable {
            echo 'Pipeline UNSTABLE'
        }

        cleanup {
            echo 'Cleanup finished'
        }
    }
}
