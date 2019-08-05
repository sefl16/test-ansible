pipeline {
  agent any
  stages {
    stage('Uninstall') {
      steps {
        ansiblePlaybook(playbook: 'playbooks/remove_mega_playbook.yaml', inventory: 'inventories/hosts', colorized: true)
      }
    }
    stage('Version check') {
      parallel {
        stage('Version check') {
          steps {
            sh 'python --version'
          }
        }
        stage('ansible check') {
          steps {
            sh 'ansible --version'
          }
        }
      }
    }
    stage('Install and config') {
      parallel {
        stage('Install and config') {
          steps {
            ansiblePlaybook(playbook: 'playbooks/mega_playbook.yaml', colorized: true, inventory: 'inventories/hosts')
          }
        }
        stage('message') {
          steps {
            echo 'Pipeline completed'
          }
        }
      }
    }
  }
}