pipeline {
    agent any
    stages {
        stage ("Pull") {
            steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                    userRemoteConfigs:[[
                        credentialsId: 'github', 
			   url: 'https://github.com/HanaBouhdida/LC.git']]])
                }
            }
        }
	stage('python test'){
            steps{
                script{
                    sh "python3 --version"
                }
            }
        }
	stage('Build'){
            steps{
                script{ 
                    sh "ansible-playbook Ansible/build.yml -i Ansible/inventory/host.yml"
                }
            }
            }
	stage('docker'){
            steps{
                script{
                    sh "ansible-playbook Ansible/docker.yml -i Ansible/inventory/host.yml"
                }
            }
        }
        stage('docker-registry'){
            steps{
                script{
                    sh "ansible-playbook Ansible/docker-registry.yml -i Ansible/inventory/host.yml"
                }
            }
        }
}
}
