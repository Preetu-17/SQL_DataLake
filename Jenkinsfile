pipeline {
    agent any

    options {
    timestamps()
    }
    
    environment {
        SQL_SERVER = "PREETU-17\\DATALAKE"
    }

    stages {

        stage('Create Database') {
            steps {
                bat '''
                sqlcmd -S %SQL_SERVER% -E -C -i CreateDB.sql
                '''
            }
        }
        // Bronze DB
        stage('Bronze - Tables') {
            steps {
                bat '''
                for %%f in (Bronze\\Tables\\*.sql) do (
                    sqlcmd -S %SQL_SERVER% -E -C -i "%%f"
                )
                '''
            }
        }

        stage('Bronze - Procedures') {
            steps {
                bat '''
                for %%f in (Bronze\\Procedures\\*.sql) do (
                    sqlcmd -S %SQL_SERVER% -E -C -i "%%f"
                )
                '''
            }
        }
        // Silver DB
        stage('Silver - Tables') {
            steps {
                bat '''
                for %%f in (Silver\\Tables\\*.sql) do (
                    sqlcmd -S %SQL_SERVER% -E -C -i "%%f"
                )
                '''
            }
        }

        stage('Silver - Procedures') {
            steps {
                bat '''
                for %%f in (Silver\\Procedures\\*.sql) do (
                    sqlcmd -S %SQL_SERVER% -E -C -i "%%f"
                )
                '''
            }
        }
        //Gold DB
        stage('Gold - Tables') {
            steps {
                bat '''
                for %%f in (Gold\\Tables\\*.sql) do (
                    sqlcmd -S %SQL_SERVER% -E -C -i "%%f"
                )
                '''
            }
        }

        stage('Gold - Views') {
            steps {
                bat '''
                for %%f in (Gold\\Views\\*.sql) do (
                    sqlcmd -S %SQL_SERVER% -E -C -i "%%f"
                )
                '''
            }
        }
    }
    post {
        success {
            echo 'Database deployment successful'
        }

        failure {
            echo 'Database deployment failed'
        }
    }    
}

