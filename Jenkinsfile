pipeline {
    agent none
    stages {
        stage('Clone Repo and Build the Flask App') {
            agent {
                label 'node1'
            }
            steps {
                echo 'Clone and Build'
                script {
                    // Clone and Build the Flask App
                    ansiblePlaybook(
                        playbook: '/home/ubuntu/Ansible-Flask/03-deploy-flaskapp.yaml',
                        inventory: '/home/centos/Ansible-Flask/hosts.ini'
                    )
                }
            }
        }
        stage('Deploy the Flask App with Ansible') {
            agent {
                label 'node1'
            }
            steps {
                echo 'Start the Flask App'
                script {
                    // Start the Flask app
                    ansiblePlaybook(
                        playbook: '/home/centos/Ansible-Flask/03-deploy.yaml',
                        inventory: '/home/centos/Ansible-Flask/hosts.ini'
                    )
                }
            }
        }
    }
}