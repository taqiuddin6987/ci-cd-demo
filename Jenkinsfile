pipeline {
    agent any
    environment {
        PROJECT_DIR = 'D:\\public_html\\extra\\CICD-Demo'
        // Server
        PROTOCOL = "http"
        PORT = 6600
        HOST = "0.0.0.0"
        DOMAIN = "http://localhost:6600"
        BASEPATH = "/api/v1"

        // Database
        DB_HOST = "localhost"
        DB_PORT = 5432
        DB_USER = "postgres"
        DB_PASSWORD = "admin"
        DATABASE = "testapp"

        // JWT
        ACCESS_JWT_SECRET = "zlwwVveUgh389JAHiM6Pne9Z89CmeutHmeTpNAvvn5e5HiqrgD26L9jKeIstPFJ3"
        ACCESS_JWT_EXPIRES_IN = "24h"
        REFRESH_JWT_SECRET = "8JZQ58q1eT2C2plHVN8rCa5dWSA37WGn4qtuh1cj0HbPHpr9yD6Y0MgT8HmkgjMf"
        REFRESH_JWT_EXPIRES_IN = "48h"
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/taqiuddin6987/ci-cd-demo.git',
                    credentialsId: 'testing'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing Node.js dependencies...'
                bat 'cd %PROJECT_DIR% && npm install'
            }
        }

        // stage('Build') {
        //     steps {
        //         echo 'Building project...'
        //         bat 'cd %WORKSPACE% && node server.js'
        //     }
        // }

        stage('Build') {
        steps {
                echo 'Building project...'
                // Run migration / seed / test instead of long-running server
                bat 'cd %PROJECT_DIR% && npm install --also=dev'
                bat 'cd %PROJECT_DIR% && npm run migrate:latest'
                bat 'cd %PROJECT_DIR% && npm run lint'
                bat 'cd %PROJECT_DIR% && npm run format'
            }
        }


        stage('Test') {
            steps {
                echo 'Running tests...'
                bat 'cd %PROJECT_DIR% && echo Tests run here'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy stage...'
                bat 'cd %PROJECT_DIR% && echo Deploy step here'
            }
        }
    }
}
