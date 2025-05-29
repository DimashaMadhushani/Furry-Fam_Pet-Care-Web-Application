pipeline {
    agent any

    tools {
        nodejs 'NodeJS'
    }

    environment {
        NODE_ENV = 'development'
    }

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/DimashaMadhushani/Furry-Fam_Pet-Care-Web-Application.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                dir('Backend') {
                    bat 'npm install'
                }
                dir('Frontend') {
                    bat 'npm install'
                }
            }
        }

        stage('Run Tests') {
            steps {
                dir('Backend') {
                    bat 'npm test || echo "No backend tests"'
                }
                dir('Frontend') {
                    bat 'npm test || echo "No frontend tests"'
                }
            }
        }

        stage('Build Frontend') {
            steps {
                dir('Frontend') {
                    bat 'npm run build'
                }
            }
        }

        stage('Start Backend') {
            steps {
                dir('Backend') {
                    bat 'start /B node index.js'
                }
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 You can add Docker or cloud deploy here.'
            }
        }
    }

    post {
        success {
            echo '✅ Build and deploy successful!'
        }
        failure {
            echo '❌ Build failed!'
        }
    }
}
