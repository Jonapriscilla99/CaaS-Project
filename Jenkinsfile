pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/SabaSB/CaaS-Project.git'
            }
        }
        
        stage('Build & Deploy EKS Cluster') {
            steps {
                script {
                    sh 'AWSCaaSProject/aws_caa_s_project/aws_caa_s_project_stack.py'
                }
            }
        }
    }
    
    post {
        success {
            echo 'EKS Cluster deployment successful!'
        }
    }
}