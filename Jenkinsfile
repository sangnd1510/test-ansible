pipeline {

    agent any
    environment {
        ANSIBLE_HOST_KEY_CHECKING = 'False'
    }
    stages {

        stage('Deploy backend app') {
           
            steps {
                withCredentials([file(credentialsId: 'drf_store_key', variable: 'drf_store_key')]) {
                    sh 'ls -la'
                    sh "cp /$drf_store_key drf_store_key"
                    sh 'cat drf_store_key'
                    sh 'ansible --version'
                    sh 'ls -la'
                    sh 'chmod 400 drf_store_key '
                    sh 'ansible-playbook -i hosts --private-key drf_store_key playbook.yml'
            }
            }
        }
        
    }
    post {
        // Clean after build
        always {
            cleanWs()
        }
    }
}