pipeline {
    agent any
    
    stages { 
        
        stage("execute_playbook") {
            steps {
                ansiblePlaybook credentialsId: '519f0365-2966-4af0-9f83-96360b212247', playbook: 'site.yml', vaultTmpPath: ''
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