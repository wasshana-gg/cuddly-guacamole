pipeline {
    agent none
    stages {
        stage('GitGuardian Scan') {
            agent {
                docker { image 'gitguardian/ggshield:1.12' }
            }
            environment {
                GITGUARDIAN_API_KEY = credentials('gitguardian-api-key')
            }
            steps {
                sh 'ggshield secret scan -v ci'
            }
        }
    }
}