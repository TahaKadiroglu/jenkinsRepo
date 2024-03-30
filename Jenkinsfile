pipeline {
  agent any
  stages {

    stage('install npm'){
      steps{
        bat '''npm install'''
      }
    }
    stage('install playwright') {
      steps {
        bat '''
          npm i -D @playwright/test
          npx playwright install
        '''
      }
    }
    stage('help') {
      steps {
        bat 'npx playwright test --help'
      }
    }
    stage('test') {
      steps {
        bat '''
          npx playwright test --list
          npx playwright test
        '''
      }
      post {
        success {
          archiveArtifacts(artifacts: 'homepage-*.png', followSymlinks: false)
          bat 'rm -rf *.png'
        }
      }
    }
  }
}
