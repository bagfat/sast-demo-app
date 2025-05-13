pipeline {
    agent any

    stages {
        stage('Install Bandit') {
            steps {
                sh 'pip install bandit'
            }
        }

        stage('Run Bandit SAST') {
            steps {
                sh 'bandit -r . -f xml -o bandit-report.xml || true'
                recordIssues tools: [bandit(pattern: 'bandit-report.xml')]
            }
        }
    }
}

