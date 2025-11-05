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
                echo 'Deploying JAR (simulated)...'
                bat 'java -cp target\\jenkins-endterm-1.0-SNAPSHOT.jar App'
            }
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
