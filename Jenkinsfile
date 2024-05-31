pipeline {
    agent any
    triggers {
        pollSCM '*/5 * * * *'
    }
    stages {
        stage('Build') {
            steps {
                sh '''
                apt update
                apt upgrade -y
                apt-get install python3 -y
                apt-get install python3-venv -y
                apt install python3-pip -y
                python3 -m venv .venv
                '''
            }
        }
        stage('Test') {
            steps {
                sh '''
                python3 -V
                . .venv/bin/activate
                pip install DateTime
                python3 py_test.py
                '''
            }
        }
        stage('Deliver') {
            steps {
                sh '''
                echo "Ready to deliver"
                '''
            }
        }
    }
}