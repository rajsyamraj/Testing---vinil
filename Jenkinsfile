node {
    stage('Checkout') {
        checkout([$class: 'GitSCM',
                  branches: [[name: '*/master']],
                  userRemoteConfigs: [[
                      url: 'https://github.com/rajsyamraj/Testing---vinil.git',
                      credentialsId: 'GIT'
                  ]]
        ])
    }

    stage('Deploy to Second VM') {
        sshagent(['GIT']) {
            sh '''
            ssh -o StrictHostKeyChecking=no jenkins@192.168.1.32 '
                cd /apps &&
                chmod +x test.sh &&
                ./test.sh
            '
            '''
        }
    }
}
