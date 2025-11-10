pipeline {
    agent any

    environment {
        WEBEX_BOT_TOKEN = credentials('webex-bot-token') // Jenkins credential ID
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Run Python Script') {
            steps {
                sh 'python3 sample_code.py'
            }
        }
    }

    post {
        success {
            echo 'Build succeeded!'
            sh """
            curl -X POST https://webexapis.com/v1/messages \
                -H "Authorization: Bearer ${WEBEX_BOT_TOKEN}" \
                -H "Content-Type: application/json" \
                -d '{"roomId":"Y2lzY29zcGFyazovL3VybjpURUFNOnVzLXdlc3QtMl9yL1JPT00vZDEzOTExZTAtYTczYy0xMWYwLTk4OTgtNWI0NTc0NGE5NDdj","text":"Build succeeded!"}'
            """
        }
        failure {
            echo 'Build failed!'
            sh """
            curl -X POST https://webexapis.com/v1/messages \
                -H "Authorization: Bearer ${WEBEX_BOT_TOKEN}" \
                -H "Content-Type: application/json" \
                -d '{"roomId":"Y2lzY29zcGFyazovL3VybjpURUFNOnVzLXdlc3QtMl9yL1JPT00vZDEzOTExZTAtYTczYy0xMWYwLTk4OTgtNWI0NTc0NGE5NDdj","text":"Build failed!"}'
            """
        }
    }
}
