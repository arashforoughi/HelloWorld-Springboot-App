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
                sh 'sudo docker build -t springboot:latest .'
            }
        }
        stage('docker tag'){
            steps{
                sh 'sudo docker tag springboot:latest 9354165450/jenkins-test:latest'
            }
        }
        stage('docker push'){
            steps{
                sh 'sudo docker push 9354165450/jenkins-test:latest'
            }
        }
        stage('create pod'){
            steps{
                sh 'sudo kubectl apply -f pod.yaml'
            }
        }
    }
}
