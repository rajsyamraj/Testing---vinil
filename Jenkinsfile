node {
    stage('Checkout') {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                  userRemoteConfigs: [[url: 'https://github.com/rajsyamraj/Testing---vinil.git']]])
    }

    stage('Deploy to Second VM') {
        sshagent(['jenkins']) {
            sh '''
            ssh -o StrictHostKeyChecking=no jenkins@192.168.1.32 '
                cd /apps &&
                git pull &&
                chmod +x test.sh &&
                ./test.sh
            '
            '''
        }
    }
}
