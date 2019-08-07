pipeline {
  agent any
  stages {
    stage('Config and Uninstall') {
      parallel {
        stage('Config and Uninstall') {
          steps {
            ansiblePlaybook(playbook: 'playbooks/remove_mega_playbook.yaml', colorized: true, inventory: 'inventories/hosts')
          }
        }
        stage('error') {
          steps {
            echo 'First step started'
          }
        }
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
    stage('Config and Install') {
      parallel {
        stage('Config and Install') {
          steps {
            ansiblePlaybook(playbook: 'playbooks/mega_playbook.yaml', colorized: true, inventory: 'inventories/hosts')
          }
        }
        stage('test_playbook') {
          steps {
            ansiblePlaybook(playbook: 'playbooks/test_playbook.yaml', colorized: true, inventory: 'inventories/hosts')
          }
        }
        stage('error') {
          steps {
            echo 'Last step started'
          }
        }
      }
    }
    stage('Test awx') {
      steps {
        ansibleTower(towerServer: 'awxDemo', jobTemplate: 'megaPlay', jobType: 'run', inventory: 'test-vm-inventory', credential: 'vm-cred', verbose: true, importTowerLogs: true)
      }
    }
  }
}