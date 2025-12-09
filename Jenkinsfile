pipeline {
    agent any

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
                bat 'cd %WORKSPACE% && npm install'
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
                bat 'cd %WORKSPACE% && npm install --also=dev'
                // bat 'cd %WORKSPACE% && npm run migrate:latest'
                bat 'cd %WORKSPACE% && npm run lint'
                bat 'cd %WORKSPACE% && npm run format'
            }
        }


        stage('Test') {
            steps {
                echo 'Running tests...'
                bat 'cd %WORKSPACE% && echo Tests run here'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy stage...'
                bat 'cd %WORKSPACE% && echo Deploy step here'
            }
        }
    }
}
