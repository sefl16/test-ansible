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
        stage('check python version') {
          steps {
            sh 'python --version'
          }
        }
        stage('check ansible version') {
          steps {
            sh 'ansible --version'
          }
        }
      }
    }
    stage('Config and Install') {
      parallel {
        stage('Config and Install') {
          steps {
            ansiblePlaybook(playbook: 'playbooks/mega_playbook.yaml', inventory: 'inventories/hosts')
          }
        }
        stage('test_playbook') {
          steps {
            ansiblePlaybook(playbook: 'playbooks/test_playbook.yaml', colorized: true, inventory: 'inventories/hosts')
          }
        }
      }
    }
    stage('Uninstall') {
      steps {
        ansiblePlaybook(playbook: 'playbooks/remove_mega_playbook.yaml', colorized: true, inventory: 'inventories/hosts')
      }
    }
  }
}