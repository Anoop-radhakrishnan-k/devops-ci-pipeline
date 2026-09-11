pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code from GitHub'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building application...'

                bat '''
                    if exist index.html (
                        echo Build Successful
                    ) else (
                        echo Build Failed
                        exit /b 1
                    )
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'

                bat '''
                    if exist test.html (
                        echo Test Passed
                    ) else (
                        echo Test Failed
                        exit /b 1
                    )
                '''
            }
        }

        stage('Validation') {
            steps {
                echo 'Running validation...'

                bat '''
                    if exist Jenkinsfile (
                        echo Jenkinsfile Validation Passed
                    ) else (
                        echo Jenkinsfile Validation Failed
                        exit /b 1
                    )
                '''

                bat '''
                    if exist index.html (
                        echo Application Validation Passed
                    ) else (
                        echo Application Validation Failed
                        exit /b 1
                    )
                '''
            }
        }
    }

    post {
        success {
            echo 'CI Pipeline completed successfully!'
        }

        failure {
            echo 'CI Pipeline failed. Check Console Output.'
        }
    }
}