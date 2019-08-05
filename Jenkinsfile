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
      parallel {
        stage('Playbooks') {
          steps {
            ansiblePlaybook(playbook: 'playbooks/mega_playbook.yaml', colorized: true, inventory: 'inventories/hosts')
            echo 'The first playbook have been executed'
          }
        }
        stage('Playbook2') {
          steps {
            ansiblePlaybook(playbook: 'playbooks/remove_mega_playbook.yaml', colorized: true, inventory: 'inventories/hosts')
          }
        }
      }
    }
  }
}