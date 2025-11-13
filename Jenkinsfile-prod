pipeline {
  agent { label 'prod-node' }
  stages {
    stage('Checkout Master Branch') {
      steps {
        git branch: 'main', url: 'https://github.com/shiyaz-ui/jenkins-demo.git'
      }
    }
    stage('Copy to Prod Server') {
      steps {
        sh '''
          mkdir -p /tmp/git_prod_copy
          cp -r * /tmp/git_prod_copy/
          echo "Prod code copied to /tmp/git_prod_copy/"
        '''
      }
    }
  }
}
