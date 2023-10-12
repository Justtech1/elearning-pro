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

        stage('Deploy Development') {
            steps {
                script {
                    dir('Development') {
                        // Deploy to the Development environment using terraform 
                        sh 'terraform init'
                        echo "Terraform action is --> ${action}"
                        sh ("terraform ${action} --auto-approve -var-file=Dev.tfvars")
                    }
                }
            }
        }
    }
}


        stage('Destroy Development') {
            steps {
                script {
                    dir('Development') {
                        // Destroy to the Development environment using terraform 
                        sh 'terraform init'
                        echo "Terraform action is --> ${action}"
                        sh ("terraform destroy --auto-approve -var-file=Dev.tfvars")
                    }
                }
            }
        }
