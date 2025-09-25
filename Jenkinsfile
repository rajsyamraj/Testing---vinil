
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/rajsyamraj/Testing---vinil.git', branch: 'master'
            }
        }

        stage('Deploy Script to Remote VM') {
            steps {
                sh 'scp -o StrictHostKeyChecking=no test.sh jenkins@192.168.1.32:/apps/'
            }
        }

        stage('Execute Script on Remote VM') {
            steps {
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
}
