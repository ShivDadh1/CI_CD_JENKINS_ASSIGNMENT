pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Setup Python') {
            steps {
                sh '''
                if ! command -v python3 &> /dev/null
                then
                    echo "Python3 not found, installing..."
                    sudo apt-get update -y
                    sudo apt-get install -y python3 python3-pip
                else
                    echo "Python3 already installed"
                fi
                '''
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
        }
        failure {
            echo 'Build failed!'
        }
    }
}
