pipeline {
    agent { label 'docker ' }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/AbdelrhmanEzzat/digi-jenkins.git'
            }
        }

        stage('Show Agent Info') {
            steps {
                sh '''
                echo "Running on EC2 Agent"
                whoami
                hostname
                pwd
                java -version
                node -v
                npm -v
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }
    }

    post {
        success {
            echo '✅ Lab 1 SUCCESS: Build ran successfully on EC2 Agent.'
        }

        failure {
            echo '❌ Lab 1 FAILED: Check the console output.'
        }

        always {
            cleanWs()
        }
    }
}
