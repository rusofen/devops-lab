pipeline {
    agent { label 'linux' }
    
    stage('Compile') {
    steps {
        sh 'mvn clean compile'
    }
}

stage('Test') {
    steps {
        sh 'mvn test'
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


