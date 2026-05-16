pipeline {
    agent any

    environment {
        SQL_SERVER = "PREETU-17\\DATALAKE"
        
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-token',
                    url: 'https://github.com/Preetu-17/SQL_DataLake.git'
            }
        }

        stage('Create Database') {
            steps {
                bat '''
                sqlcmd -S %SQL_SERVER% -E -C -i CreateDB.sql
                '''
            }
        }

        
            }
}
