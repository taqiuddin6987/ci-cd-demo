pipeline {
    agent any
    environment {
        PROJECT_DIR = 'D:\\public_html\\extra\\CICD-Demo'
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
