pipeline{
    agent any
    tools{
        ansible 'ansible'
    }
    stages{
        stage('clean work space'){
            steps{
                cleanWs()
            }
        }
        stage('git checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/mukeshr-29/ansible-project.git'
            }
        }
        stage('trivy filescan'){
            steps{
                sh 'trivy fs .'
            }
        }
        stage('ansible provisioning'){
            steps{
                ansiblePlaybook installation: 'ansible', playbook: 'playbook.yml'
            }
        }
    }
}
