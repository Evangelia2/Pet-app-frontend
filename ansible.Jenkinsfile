pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/<username>/<repository>.git'
            }
        }

        stage('Run Ansible') {
            steps {
                sh 'ansible-playbook -i inventory.ini ansible-compose.yml'
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'curl -f http://192.168.56.101:8080 || exit 1'
            }
        }
    }
}
