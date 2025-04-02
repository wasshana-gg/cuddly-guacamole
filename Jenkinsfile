pipeline {
    agent { docker { image 'gitguardian/ggshield:v1.38.1' } }
        
    stages {
        stage('GitGuardian Scan') {
            environment {
                CI = 'true'
            }
            steps {
                echo "Starting analysis with GitGuardian"
                withCredentials([string(credentialsId: 'gitguardian-api-key', variable: 'GITGUARDIAN_API_KEY')]) {
                    sh 'ggshield --version'
                    sh 'ggshield secret scan -v ci'
                }
            }
        }
    }
}
