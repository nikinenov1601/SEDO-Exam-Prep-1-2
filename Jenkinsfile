pipeline {
    agent any

    environment {
        DOTNET_ROLL_FORWARD = 'Major'
    }

    stages {
        stage('Restore dependencies') {
            when { anyOf { branch 'main'; branch 'feature'; branch 'feature/*' } }
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build the project') {
            when { anyOf { branch 'main'; branch 'feature'; branch 'feature/*' } }
            steps {
                bat 'dotnet build --no-restore'
            }
        }

        stage('Run tests') {
            when { anyOf { branch 'main'; branch 'feature'; branch 'feature/*' } }
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
