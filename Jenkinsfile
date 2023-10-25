pipeline {
    agent { label 'jenkins-slave node' }
    environment {
        docker_pwd = credentials ('docker hub_jenkins_cred')
    }
    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
               git branch: 'main', url: 'https://github.com/pavan1026/apache.git'
            }
        }
         
        stage('Docker image build') {
            steps {
                script {
                    sh 'docker build -t 8179554905/apache:$BUILD_NUMBER .'
                }
            }
            
        }       
        stage('Docker login and push') {
            steps {
                script {
                 sh 'echo $docker_pwd_PSW | docker login -u $docker_pwd_USR --password-stdin'   
                }
            }
        }    
        stage('latest image of docker') {
            steps {
                script {
                 sh 'docker push 8179554905/apache:$BUILD_NUMBER'   
                }
            }
            
        }
        
        
    }
    
}

