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
      	        withCredentials([usernamePassword(credentialsId: 'DockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
        	    sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
                sh 'docker push my-portfolio'
                }
            }
        }
        
        
    }
}
