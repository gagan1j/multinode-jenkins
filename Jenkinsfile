pipeline {
    agent any

    environment {
        APP_NAME = 'your-app-name'
        GIT_REPO_URL = 'https://github.com/gagan1j/multinode-jenkins'
    }

    stages {
        stage('Checkout SCM') {
            steps {
                echo "Checking out the repository..."
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                echo "Installing dependencies..."
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                bat 'python -m unittest discover'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying application..."
                // Add any deployment steps needed for your Flask app here
            }
        }

        stage('Run Application') {
            steps {
                echo "Running the application..."
                // Example for running a Flask app on Windows
                bat 'python app.py'
            }
        }
    }

    post {
        always {
            echo "Pipeline completed."
        }
        success {
            echo "Build and deployment successful."
        }
        failure {
            echo "There was a failure during the pipeline execution."
        }
    }
}

