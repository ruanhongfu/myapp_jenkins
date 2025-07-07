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
                python3 -m venv venv
                source venv/bin/activate
                pip install -r requirements.txt
                '''
            }
        }

        stage('Run tests') {
            steps {
                sh '''
                source venv/bin/activate
                pytest test_app.py
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                source venv/bin/activate
                nohup python app.py &
                '''
            }
        }
    }
}

