pipeline {
    agent {
        docker {
            image 'mcr.microsoft.com/dotnet/sdk:8.0'
            args '-u root:root'
        }
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/microsoft/dotnet.git'
            }
        }
        stage('Restore') {
            steps {
                sh 'dotnet restore'
            }
        }
        stage('Build') {
            steps {
                sh 'dotnet build --no-restore'
            }
        }
        stage('Test') {
            steps {
                sh 'dotnet test --no-build'
            }
        }
        stage('Publish') {
            steps {
                sh 'dotnet publish --no-build -o out'
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: '**/out/**', allowEmptyArchive: true
        }
        failure {
            mail to: 'your-email@example.com',
                 subject: 'Build failed: ${currentBuild.fullDisplayName}',
                 body: 'Something is wrong with the build ${env.BUILD_URL}'
        }
    }
}

