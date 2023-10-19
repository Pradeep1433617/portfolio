pipeline {
    agent any
    stages {
        stage('Cloning') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'Github', url: 'https://github.com/Pradeep1433617/portfolio.git']])
            }
        }
        
        
    }
}
