pipeline {
    agent { docker { image 'gitguardian/ggshield:v1.27.0' } }
        
    stages {
        stage('GitGuardian Secrets Scan') {
            environment {
                CI = 'true'
            }
            steps {
                echo "Starting analysis with GitGuardian"
                withCredentials([string(credentialsId: 'gitguardian-api-key', variable: 'GITGUARDIAN_API_KEY')]) {
                    sh 'git config --global --add safe.directory \'*\''
                    sh 'git config -l'
                    sh 'ggshield --version'
                    sh 'ggshield secret scan -v --debug ci'
                }
            }
        }
    }
}
