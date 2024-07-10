pipeline {
    agent any

    environment {
        SOLUTION_NAME = 'YourSolution.sln'
        TEST_PROJECT_NAME = 'YourTestProject.dll'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Hclishikawa/dotnet.git'
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
