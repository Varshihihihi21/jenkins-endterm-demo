pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // 🔹 Replace with your actual GitHub URL
                git url: 'https://github.com/Varshihihihi21/jenkins-endterm-demo.git', branch: 'main'

            }
        }

        stage('Build') {
            steps {
                echo 'Building project...'
                bat 'mvn clean compile'
            }
        }

        stage('Unit Test') {
            steps {
                echo 'Running tests...'
                bat 'mvn test'
            }
        }

        stage('SonarQube Analysis') {
            when {
                expression { return false } // change to true when SonarQube setup is ready
            }
            steps {
                echo 'SonarQube analysis would run here.'
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging application...'
                bat 'mvn package'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Starting Deployment...'
                bat 'if not exist C:\\deploy mkdir C:\\deploy'
                bat 'copy target\\*.jar C:\\deploy\\ /Y'
                echo 'Deployment successful! JAR copied to C:\\deploy'
            }
    }

    post {
        success {
            echo '✅ Pipeline completed successfully!'
        }
        failure {
            echo '❌ Pipeline failed!'
        }
    }
}
