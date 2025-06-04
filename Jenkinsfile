pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/bagfat/sast-demo-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install bandit'
            }
        }

        stage('SAST Analysis') {
            steps {
                sh 'bandit -f xml -o bandit-output.xml -r . || true'
            }
        }

        stage('Archive Results') {
            steps {
                archiveArtifacts artifacts: 'bandit-output.xml', allowEmptyArchive: true
            }
        }
    }
}

