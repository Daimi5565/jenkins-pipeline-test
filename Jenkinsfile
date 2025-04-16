pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                git branch: 'main', credentialsId: 'github-ssh-key', url: 'git@github.com:Daimi5565/jenkins-pipeline-test.git'
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run the application') {
            steps {
                sh 'nohup npm start > app.log 2>&1 &'
                echo '✅ Application is running on port 3000'
            }
        }
    }

    post {
        failure {
            echo '❌ Build failed!'
        }
        success {
            echo '✅ Build completed successfully!'
        }
    }
}
