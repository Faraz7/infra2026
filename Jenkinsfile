pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'git@github.com:faraz-cloudops-org/frz_infra2026.git',
                    credentialsId: 'git-ssh-key'
            }
        }

        stage('Terraform Init & Apply') {
            steps {
                sh '''
                cd gcp
                terraform init
                terraform plan -out=tfplan
                terraform apply -auto-approve tfplan
                '''
            }
        }
    }
}