pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Checkout') { // ⚠️ Giai đoạn này quan trọng để lấy code từ Git
            steps {
                git branch: 'main', 
                    credentialsId: 'github-token', 
                    url: 'https://github.com/vominh-source/bt2-pipeline.git'
            }
        }

        stage('Build') {
            steps {
                echo "Building.."
                bat '''
                python -m pip install -r requirements.txt
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                bat '''
                cd myapp
                python hello.py
                python hello.py --name=Brad
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                bat '''
                echo "doing delivery stuff.."
                '''
            }
        }
    }
}
