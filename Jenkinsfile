// Reference: https://plugins.jenkins.io/ansible/
pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git credentialsId: 'github_token', url: 'https://github.com/dbasak2013/jenkins-gcp-ansible.git'
            }
        }
        
        stage('GCP') {
            environment {
                gcp_cred_file=credentials("gcp_service_account")
            }
            steps {
                // withCredentials([file(credentialsId: 'gcp_service_account', variable: 'gcp_cred_file')]) {
                //     writeFile file: 'key/private.json', text: readFile(gcp_cred_file)
                //     sh "ansible-playbook -vvv gcp_playbook.yml"
                // }
                sh "ansible-playbook -vvv gcp_playbook.yml"
            }
            /*post {
                always {
                    sh "rm -rf ./key/"
                }
            }*/
        }
    }
}
