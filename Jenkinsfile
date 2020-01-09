pipeline {
    agent {
        docker {
            image 'node:6-alpine' 
            args '-p 3000:3000' 
        }
    }
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
