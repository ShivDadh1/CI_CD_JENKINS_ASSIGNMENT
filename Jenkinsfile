pipeline {
    agent any

    triggers {
        githubPush() // Allows GitHub webhook to trigger build
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/ShivDadh1/CI_CD_JENKINS_ASSIGNMENT.git'
            }
        }

        stage('Run Python') {
            steps {
                bat 'python sample_code.py'
            }
        }
    }

    post {
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
