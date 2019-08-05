pipeline {
  agent any
  stages {
    stage('Initialize') {
      parallel {
        stage('Initialize') {
          steps {
            echo 'Hello world!'
          }
        }
        stage('pwd') {
          steps {
            sh 'pwd'
          }
        }
      }
    }
    stage('Playbook') {
      steps {
        ansiblePlaybook(playbook: 'playbooks/mega_playbook.yaml', colorized: true, inventory: 'inventories/hosts')
      }
    }
  }
}