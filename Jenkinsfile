pipeline {
    agent none
    stages {
        stage('Test Deployment') {
            agent { label 'test-node' }
            steps {
                echo 'Deploying code to Test Server...'
                sh '''
                rm -rf /home/ubuntu/test-deploy
                mkdir -p /home/ubuntu/test-deploy
                cp -r * /home/ubuntu/test-deploy/
                echo "Code deployed to Test server on $(date)" > /home/ubuntu/test-deploy/deploy_log.txt
                '''
            }
        }

        stage('Production Deployment') {
            when {
                expression { currentBuild.currentResult == 'SUCCESS' }
            }
            agent { label 'prod-node' }
            steps {
                echo 'Deploying code to Prod Server...'
                sh '''
                rm -rf /home/ubuntu/prod-deploy
                mkdir -p /home/ubuntu/prod-deploy
                cp -r * /home/ubuntu/prod-deploy/
                echo "Code deployed to Prod server on $(date)" > /home/ubuntu/prod-deploy/deploy_log.txt
                '''
            }
        }
    }
}
