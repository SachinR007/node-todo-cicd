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
                sh 'docker build -t todo-app .'
            }
        }
        
        stage('deploy'){
            steps{
                sh 'docker run -it -d -p 8000:8000 todo-app'
            }
            
        }
        
    }
}
