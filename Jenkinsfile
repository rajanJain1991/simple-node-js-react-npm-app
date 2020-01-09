pipeline {
    agent any
    
    environment {
        CI = 'true'
    }
    stages {

        stage('Build') { 
            steps {
                sshagent (credentials: ['dev-test-server-ssh-access']) {
                    sh "ssh -vvv -o StrictHostKeyChecking=no -T ubuntu@35.158.52.243"
                    sh "ls"
                } 
            }
        }
    }
}
