pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/ruanhongfu/myapp_jenkins.git'
            }
        }

        stage('Install dependencies') {
            steps {
                sh '''
                #!/bin/bash
                set -e
                python3 -m venv venv
                . venv/bin/activate
                pip install -r requirements.txt
                '''
            }
        }

        stage('Run tests') {
            steps {
                sh '''
                #!/bin/bash
                set -e
                . venv/bin/activate
                pytest test_app.py
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                #!/bin/bash
                set -e
                . venv/bin/activate
                nohup python app.py &
                '''
            }
        }
    }
}

