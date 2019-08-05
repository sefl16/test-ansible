pipeline {
  agent any
  stages {
    stage('Initialize') {
      steps {
        echo 'Hello world!'
      }
    }
    stage('Playbook') {
      steps {
        ansiblePlaybook(playbook: 'playbooks/mega_playbook.yaml', colorized: true, inventory: 'inventories/hosts')
      }
    }
  }
}