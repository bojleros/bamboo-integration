pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        script {
          env.RELEASE_SCOPE = input message: 'Deploy to STAGING ?', ok: 'Confirm', parameters: [choice(name: 'DEPLOY_STAGING', choices: 'Yes\nNo', description: 'Make deployment to STAGING ENV ?')]
        }
        echo "${env.DEPLOY_STAGING}"
      }
    }
    stage('Test') {
      steps {
        echo 'Test'
      }
    }
    stage('Deploy Staging') {
      steps {
        script {
          if (env.BRANCH_NAME == 'master') {
            echo 'Deploy to STAGING'
          } else {
            echo 'I execute elsewhere'
          }
        }
        
      }
    }
    stage('Deploy Production') {
      steps {
        echo 'production'
      }
    }
  }
  environment {
    SLACK_WEBHOOK_URL = 'https://hooks.slack.com/services/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'
    JIRA_PROJECT = 'BLT'
  }
  options {
    buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '5'))
  }
}