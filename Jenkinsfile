pipeline {
    agent { docker { image 'gitguardian/ggshield:v1.12.0' } }
        
    stages {
        stage('GitGuardian Scan') {
            environment {
                CI = 'true'
            }
            steps {
                echo "Starting analysis with GitGuardian"
                withCredentials([string(credentialsId: 'gitguardian-api-key', variable: 'GITGUARDIAN_API_KEY')]) {
                    sh 'ggshield scan -v ci'
                }
            }
        }
    }
}
