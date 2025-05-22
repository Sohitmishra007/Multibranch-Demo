pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
                echo "Checked out branch: ${env.BRANCH_NAME}"
            }
        }

        stage('Build') {
            steps {
                echo "Setting up Python environment and installing dependencies..."
                script {
                    sh '''
                        python3 -m venv venv
                        . venv/bin/activate
                        pip install -r requirements.txt
                    '''
                    echo "Python dependencies installed."
                }
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                script {
                    sh '''
                        . venv/bin/activate
                        echo "No specific tests defined for this demo, but this is where they would run."
                    '''
                }
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                echo "Deploying application from main branch..."
                script {
                    sh '''
                        . venv/bin/activate

                        # Stop any app running on port 5000 (ignore error if none)
                        fuser -k 5000/tcp || true

                        # Start Flask app in background, redirect logs
                        FLASK_APP=app.py FLASK_RUN_HOST=0.0.0.0 FLASK_RUN_PORT=5000 nohup python -m flask run > app.log 2>&1 &
                    '''
                    echo "Flask application started on port 5000."
                    echo "Please ensure port 5000 is open in your server's firewall/security group."
                }
            }
        }
    }
}
