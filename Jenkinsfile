pipeline {
    agent any
    
    stages { 

        stage('Run Playbook 1') {
            when {
                changeset 'playbook/playbook1.yml'
            }
            steps {
                ansiblePlaybook credentialsId: '519f0365-2966-4af0-9f83-96360b212247', playbook: 'playbook/playbook1.yml', vaultTmpPath: ''
            }
        }
        stage('Run Playbook 1') {
            when {
                changeset 'playbook/playbook2.yml'
            }
            steps {
                ansiblePlaybook credentialsId: '519f0365-2966-4af0-9f83-96360b212247', playbook: 'playbook/playbook2.yml', vaultTmpPath: ''
            }
        }  
        
        stage('Run Playbook 1') {
            when {
                changeset 'playbook/playbook3.yml'
            }
            steps {
                ansiblePlaybook credentialsId: '519f0365-2966-4af0-9f83-96360b212247', playbook: 'playbook/playbook3.yml', vaultTmpPath: ''
            }
        }
    }

    post {
        always {
            emailext body: "${env.BUILD_URL}\n${currentBuild.absoluteUrl}",
                to: 'always@foo.bar',
                recipientProviders: [previous()],
                subject: "${currentBuild.currentResult}: Job ${env.JOB_NAME} [${env.BUILD_NUMBER}]"
        }
        
    } 
}