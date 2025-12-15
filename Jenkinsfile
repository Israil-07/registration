pipeline {
    agent any

    stages {

        stage('Check files') {
            steps {
                sh 'ls -l'
            }
        }

        stage('Docker compose build') {
            steps {
                echo 'Building services using docker compose'
                sh 'docker compose build'
            }
        }

        stage('Container start') {
            steps {
                echo 'Starting container'
                sh 'docker compose down || true'
                sh 'docker compose up -d'
            }
        }

        stage('Test') {
            steps {
                echo 'Application deployed successfully'
            }
        }
    }

    post {
        success {
            echo '✅ BUILD SUCCESS: Application deployed successfully'
        }

        failure {
            echo '❌ BUILD FAILED: Please check Jenkins logs'
        }

        always {
            echo 'ℹ️ Pipeline execution completed'
        }
    }
}
