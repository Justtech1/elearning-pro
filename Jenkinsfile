pipeline {
    agent any
    tools {
        terraform 'Terraform project'
    }

    stages {
        stage('checkout') {
            steps {
                // Checkout the code from github repo
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Justtech1/elearning-pro.git']])
        }
    }    

        stage('Deploy Production') {
            steps {
                script {
                    dir('Production') {
                        // Deploy to the Production environment using terraform 
                        sh 'terraform init'
                        echo "Terraform action is --> ${action}"
                        sh ("terraform ${action} --auto-approve -var-file=Prod.tfvars")
                    }
                }
            }
        }
    }
}