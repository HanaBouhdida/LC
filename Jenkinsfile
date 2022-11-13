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
}
}
