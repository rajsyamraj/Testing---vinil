pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/rajsyamraj/Testing---vinil.git'
            }
        }

        stage('Deploy to Second VM') {
            steps {
                sshagent(['your-ssh-credential-id']) {
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
    }

    post {
        success {
            echo 'Deployment completed successfully!'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
}
