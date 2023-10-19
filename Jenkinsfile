pipeline {
    agent any
    stages {
        stage('Cloning') {
            steps {
                checkout scmGit(branches: [[name: '*/testing']], extensions: [], userRemoteConfigs: [[credentialsId: 'Github', url: 'https://github.com/Pradeep1433617/portfolio.git']])
            }
        }
        stage('Docker Image'){
            steps{
                sh 'docker build -t my-portfolio .'
            }

        }
        stage('Build and Run Conatiner'){
            steps{
                sh 'docker run -d -p 8082:80 my-portfolio .'
            }

        }
        stage('Docker Push') {
            steps {
      	        withCredentials([usernamePassword(credentialsId: 'DockerHub')]) {
        	    sh 'docker login -u $USERNAME -p $PASSWORD'
                
                sh 'docker push my-portfolio'
                }
            }
        }
        
        
    }
}
