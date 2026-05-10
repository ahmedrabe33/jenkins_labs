pipeline {
    agent { label 'node-agent' }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/ahmedrabe33/jenkins_labs.git'
            }
        }

        stage('Show Agent Info') {
            steps {
                sh '''
                export NVM_DIR="$HOME/.nvm"
                . "$NVM_DIR/nvm.sh"

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
                sh '''
                export NVM_DIR="$HOME/.nvm"
                . "$NVM_DIR/nvm.sh"

                npm install
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                export NVM_DIR="$HOME/.nvm"
                . "$NVM_DIR/nvm.sh"

                npm test
                '''
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