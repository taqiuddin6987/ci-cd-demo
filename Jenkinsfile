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

        stage('Build') {
            steps {
                echo 'Building project...'
                // Windows ke liye batch command
                bat 'node server.js'   // Agar Node.js project hai
                // Python project ke liye: bat 'python script.py'
                // Java project ke liye: bat 'javac Main.java'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Windows batch test command
                bat 'echo Running tests...'  
                // Replace with actual test command
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy stage...'
                // Optional deploy commands
                bat 'echo Deploy step here...' 
            }
        }
    }
}
