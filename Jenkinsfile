pipeline {
    agent any

    stages {

        stage('Check Terraform') {
            steps {
                sh 'terraform version'
            }
        }

        stage('Git Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/Alanatk/terraform-jenkins.git'
            }
        }

        stage('Terraform Init') {
            steps {
                sh 'terraform init'
            }
        }

        stage('Terraform Validate') {
            steps {
                sh 'terraform validate'
            }
        }

        stage('Terraform Plan') {
            steps {
                sh 'terraform plan'
            }
        }

        stage('Terraform Apply') {
            steps {
                sh 'terraform apply -auto-approve'
            }
        }
    }

    post {
        success {
            echo 'Terraform Deployment Successful'
        }

        failure {
            echo 'Terraform Deployment Failed'
        }
    }
}
