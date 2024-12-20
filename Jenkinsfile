pipeline {
    agent any

    environment {
        // Repository and deployment variables
        ANSIBLE_INVENTORY = 'ansible/inventory/hosts.yml'
        ANSIBLE_SITE_YML_PATH = "ansible/site.yml"
    }

    stages {
        stage('Run Ansible Playbook') {
            steps {
                sh """
                set -x
                     ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i ${ANSIBLE_INVENTORY} ${ANSIBLE_SITE_YML_PATH} \
                     -v
                """
            }
        }
    }

    post {
        always {
            cleanWs()
        }
        success {
            echo 'Deployment completed successfully!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
