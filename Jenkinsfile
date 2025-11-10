pipeline {
    agent {
        docker {
            image 'python:3.11'   // Official Python image with Python pre-installed
            args '-u root:root'    // Run as root inside container to avoid permission issues
        }
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Run Python Script') {
            steps {
                // Run your Python script
                sh 'python sample_code.py'
            }
        }
    }

    post {
        success {
            echo 'Build succeeded!'
            // Add WebEx notification here if needed later
        }
        failure {
            echo 'Build failed!'
            // Add WebEx notification here if needed later
        }
    }
}
