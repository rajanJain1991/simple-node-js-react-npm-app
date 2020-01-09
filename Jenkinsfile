pipeline {
    agent {
        docker {
            image 'node'
            args '-p 3000:3000'
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sshagent (credentials: ['dev-test-server-ssh-access']) {
                    sh "ssh -vvv -o StrictHostKeyChecking=no -T ubuntu@35.158.52.243"
                    sh "ls"
                }
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
