pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                git 'git@github.com:Daimi5565/jenkins-pipeline-test.git'
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run the application') {
            steps {
                sh 'nohup npm start &'
                echo 'Application is running on port 3000'
            }
        }
    }
}
