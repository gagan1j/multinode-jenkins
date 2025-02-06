pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                script {
                    echo 'Checking out the repository...'
                    checkout scm
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    echo 'Installing dependencies...'
                    sh 'python -m venv venv && source venv/bin/activate && pip install -r requirements.txt'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    echo 'Running unit tests...'
                    sh 'pytest tests/'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo 'Deploying the application...'
                    sh 'nohup python app.py &'
                }
            }
        }

        stage('Run Application') {
            steps {
                script {
                    echo 'Starting the application...'
                    sh 'python app.py'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the logs for details.'
        }
    }
}

