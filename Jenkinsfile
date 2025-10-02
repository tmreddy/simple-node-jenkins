pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                git branch: 'main', url: 'https://github.com/tmreddy/simple-node-jenkins.git'
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                // If no tests, just echo
                sh 'echo "No tests configured"'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                pm2 stop simple-node-jenkins || true
                pm2 start index.js --name simple-node-jenkins
                pm2 save
                '''
            }
        }
    }
}
