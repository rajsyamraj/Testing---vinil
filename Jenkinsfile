stage('Deploy to Second VM') {
    steps {
        sshagent(['second-vm-ssh']) {
            sh '''
            ssh -o StrictHostKeyChecking=no jenkins@192.168.1.32 '
                cd /apps/ &&
                git pull &&
                chmod +x test.sh &&
                ./test.sh
            '
            '''
        }
    }
}
