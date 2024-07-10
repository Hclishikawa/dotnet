pipeline {
    agent any

    environment {
        SOLUTION_NAME = 'bcreadgen'

    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Hclishikawa/dotnet.git'
            }
        }

        stage('Restore NuGet Packages') {
            steps {
                sh 'dotnet restore ${SOLUTION_NAME}'
            }
        }

        stage('Build') {
            steps {
                sh 'dotnet build ${SOLUTION_NAME} -c Release'
            }
        }
    }
}
