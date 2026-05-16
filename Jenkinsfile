pipeline {
    agent any

    environment {
        SQL_SERVER = "localhost"
        
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/Preetu-17/SQL_DataLake.git'
            }
        }

        stage('Create Database') {
            steps {
                bat '''
                sqlcmd -S %SQL_SERVER% -E -i CreateDB.sql
                '''
            }
        }

        
            }
}
