pipeline {
    agent any

    stages {
        stage('Code from repo') {
            steps{
                git url: 'https://github.com/SachinR007/node-todo-cicd.git', branch: 'master' 
            }
        }
        stage('build')
        {
            steps{
                sh 'docker build -t sachin2802/todo-app:latest .'
            }
        }
        
        stage('Push to dockerhub')
        {
            steps{
                
             withCredentials([usernamePassword(credentialsId: 'DockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
                 
                 sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
                  sh "docker push ${env.dockerHubUser}/todo-app:latest"
             }
                
            }
        }
        
        stage('deploy')
        {
           steps{
            sh "docker-compose down"
           }
        }
        
        
    }
}
