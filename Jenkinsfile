pipeline {
    agent any

    environment {
        // You can define environment variables here if needed
        NODE_ENV = 'development'
    }

    stages {
        stage('Clone repository') {
            steps {
                // Use SSH credentials with ID 'github-ssh-key'
                git credentialsId: 'github-ssh-key', url: 'git@github.com:Daimi5565/jenkins-pipeline-test.git'
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
                echo '✅ Application is running in the background on port 3000'
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
