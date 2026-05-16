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
                for %%f in (sql\\Bronze\\tables\\*.sql) do (
                    sqlcmd -S %SQL_SERVER% -E -C -i "%%f"
                )
                '''
            }
        }

        stage('Bronze - Procedures') {
            steps {
                bat '''
                for %%f in (sql\\Bronze\\procedures\\*.sql) do (
                    sqlcmd -S %SQL_SERVER% -E -C -i "%%f"
                )
                '''
            }
        }
        // Silver DB
        stage('Silver - Tables') {
            steps {
                bat '''
                for %%f in (sql\\Silver\\tables\\*.sql) do (
                    sqlcmd -S %SQL_SERVER% -E -C -i "%%f"
                )
                '''
            }
        }

        stage('Silver - Procedures') {
            steps {
                bat '''
                for %%f in (sql\\Silver\\procedures\\*.sql) do (
                    sqlcmd -S %SQL_SERVER% -E -C -i "%%f"
                )
                '''
            }
        }
        //Gold DB
        stage('Gold - Tables') {
            steps {
                bat '''
                for %%f in (sql\\Gold\\tables\\*.sql) do (
                    sqlcmd -S %SQL_SERVER% -E -C -i "%%f"
                )
                '''
            }
        }

        stage('Gold - Views') {
            steps {
                bat '''
                for %%f in (sql\\Gold\\views\\*.sql) do (
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

