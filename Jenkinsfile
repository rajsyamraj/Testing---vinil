stage('Deploy to Second VM') {
    steps {
        sshagent(['second-vm-ssh']) {
            sh '''
            ssh -o StrictHostKeyChecking=no jenkins@192.168.1.32 '
                cd /home/jenkins/deployment &&
                git pull &&
                chmod +x deploy.sh &&
                ./deploy.sh
            '
            '''
        }
    }
}
