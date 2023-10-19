pipeline {
    agent any
    stages {
        stage('Cloning') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'Github', url: 'https://github.com/Pradeep1433617/portfolio.git']])
            }
        }
        stage('Docker Image'){
            steps{
                sh 'docker build -t personal .'
            }

        }
        stage('Build and Run Conatiner'){
            steps{
                sh 'docker run -d -p 8081:80 personal .'
            }

        }
        
        
    }
}
