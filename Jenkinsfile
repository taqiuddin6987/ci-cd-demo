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

        stage('Load Environment File') {
            steps {
                echo "Loading .env file from Jenkins Credential..."

                withCredentials([file(credentialsId: 'ENV_FILE', variable: 'ENVFILE')]) {
                    bat """
                        cd %PROJECT_DIR%
                        copy /Y %ENVFILE% .env
                    """
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing Node.js dependencies...'
                bat 'cd %PROJECT_DIR% && npm install'
            }
        }

        stage('Build') {
            steps {
                echo 'Running build steps...'
                bat 'cd %PROJECT_DIR% && npm install --also=dev'
                bat "cd %PROJECT_DIR% && npm run migrate:latest"
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
                echo 'Deploying...'
                bat 'cd %PROJECT_DIR% && echo Deployment step here'
            }
        }
    }
}
