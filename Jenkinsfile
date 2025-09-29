pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                git branch: 'main', url: 'https://github.com/<your-username>/node-jenkins-app.git'
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
                // Kill old process (if running) and restart app
                sh '''
                pkill -f "node index.js" || true
                nohup npm start > app.log 2>&1 &
                '''
            }
        }
    }
}
