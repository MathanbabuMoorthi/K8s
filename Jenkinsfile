pipeline {
    agent any
    
    stages {
        stage('Clean Workspace') {
            steps {
                script {
                    deleteDir()
                }
            }
        }
        
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Image build'){
            steps{
                script{
                    bat 'docker build -t mathanbabumoorthi/battle-img:v2 .'
                }
            }
        }
        stage('Docker Push'){
            steps{
                script{
                    withCredentials([string(credentialsId: 'docker-hub', variable: 'dokcer-hub')]) {
                    bat 'docker login -u mathanbabumoorthi -p ${docker-hub}'
                    }
                    bat 'docker push mathanbabumoorthi/battle-img:v2'
                }
            }
        }
    }
}
