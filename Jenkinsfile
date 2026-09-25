pipeline {
    agent any

    environment {
        DEPLOY_DIR = 'C:\\JenkinsDeploy'
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Cloning project from GitHub...'
                git branch: 'main',
                    url: 'https://github.com/ShreyaKharade/Jenkins-Experiment-6'
            }
        }

        stage('Build') {
            steps {
                echo 'Build Step: Checking web application files...'
                bat 'dir'
            }
        }

        stage('Test') {
            steps {
                echo 'Test Step: Checking required files...'
                bat 'if exist index.html (echo index.html found) else (exit /b 1)'
                bat 'if exist style.css (echo style.css found) else (exit /b 1)'
                bat 'if exist script.js (echo script.js found) else (exit /b 1)'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying web application...'

                bat 'if not exist "%DEPLOY_DIR%" mkdir "%DEPLOY_DIR%"'

                bat 'xcopy /Y /E index.html style.css script.js "%DEPLOY_DIR%\\"'
            }
        }
    }

    post {
        success {
            echo 'Pipeline finished successfully!'
            echo 'Web application deployed to C:\\JenkinsDeploy'
        }

        failure {
            echo 'Pipeline failed! Check build logs.'
        }
    }
}