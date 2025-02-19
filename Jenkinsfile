pipeline {
    agent any

    environment {
        PYTHON_HOME = '/usr/bin/python3'  // Adjust the Python installation path based on your environment
        PATH = "${env.PYTHON_HOME}:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the repository from GitHub, always from the 'main' branch
                git branch: 'main', url: 'https://github.com/sireeshamarri/git-recruiment.git'
            }
        }

        stage('Setup Python') {
            steps {
                script {
                    // Optionally, you can create a virtual environment here if needed
                    // sh 'python3 -m venv venv'
                    // sh './venv/bin/pip install -r requirements.txt'

                    // Ensure the right Python version is installed and ready
                    sh 'python3 --version'
                }
            }
        }

        stage('Run Python Script') {
            steps {
                script {
                    // Run the Python script (ensure the file path is correct within the repository)
                    sh 'python3 python.py'  // Adjust if the script is in a subfolder or needs specific args
                }
            }
        }
    }

    post {
        always {
            // Clean up actions, if any (e.g., removing virtual environments)
            echo 'Pipeline finished'
        }

        success {
            echo 'Python script executed successfully!'
        }

        failure {
            echo 'Something went wrong with the execution.'
        }
    }
}

