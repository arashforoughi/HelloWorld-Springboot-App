pipeline{
    agent any
    
    stages{
        stage('Git clone'){
            steps{
                git 'https://github.com/arashforoughi/HelloWorld-Springboot-App.git'
            }
        }
        stage('maven build'){
            steps{
                sh 'mvn package'
            }
        }
        stage('Create Dockerimage'){
            steps{
                sh 'sudo docker build -t 9354165450/springboot:${BUILD_NUMBER} .'
            }
        }
        stage('docker push'){
            steps{
                sh 'sudo docker push 9354165450/springboot:${BUILD_NUMBER}'
            }
        }
        stage('docker tag'){
            steps{
                sh 'sudo docker tag 9354165450/springboot:${BUILD_NUMBER} springboot:latest'
            }
        }
        stage('create pod'){
            steps{
                sh 'sudo docker compose up -d'
            }
        }
    }
}
