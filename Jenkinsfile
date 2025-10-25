pipeline {
  agent { label 'test-node' }
  stages {
    stage('Checkout Test Branch') {
      steps {
        git branch: 'test', url: 'https://github.com/shiyaz-ui/jenkins-demo.git'
      }
    }
    stage('Copy to Test Server') {
      steps {
        sh '''
          mkdir -p /tmp/git_test_copy
          cp -r * /tmp/git_test_copy/
          echo "Test code copied to /tmp/git_test_copy/"
        '''
      }
    }
  }
}
