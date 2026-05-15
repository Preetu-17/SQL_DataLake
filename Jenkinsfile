pipeline {
    agent any

    environment {
        SQL_SERVER = "localhost"
        DB_USER = "PREETU-17\Preetu"
        DB_PASS = "Preetu@1791"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/Data_Warehouse/SQL-DataLake.git'
            }
        }

        stage('Create Database') {
            steps {
                bat """
                sqlcmd -S %SQL_SERVER% -U %DB_USER% -P %DB_PASS% -i CreateDB.sql
                """
            }
        }

        stage('Create Tables') {
            steps {
                bat """
                for %%f in (Tables\\*.sql) do (
                    sqlcmd -S %SQL_SERVER% -U %DB_USER% -P %DB_PASS% -d SalesDB -i %%f
                )
                """
            }
        }

        stage('Create Procedures') {
            steps {
                bat """
                for %%f in (Procedures\\*.sql) do (
                    sqlcmd -S %SQL_SERVER% -U %DB_USER% -P %DB_PASS% -d SalesDB -i %%f
                )
                """
            }
        }
    }
}