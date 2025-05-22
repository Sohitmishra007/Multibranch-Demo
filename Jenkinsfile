// Jenkinsfile

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
                    // Create a Python virtual environment
                    sh 'python3 -m venv venv'
                    // Activate the virtual environment and install dependencies
                    sh 'set +x; source venv/bin/activate; set -x; pip install -r requirements.txt'
                    echo "Python dependencies installed."
                }
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                script {
                    sh 'set +x; source venv/bin/activate; set -x;'
                    sh 'echo "No specific tests defined for this demo, but this is where they would run."'
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
                    // 1. Activate the virtual environment
                    sh 'set +x; source venv/bin/activate; set -x;'

                    // 2. Stop any previously running instance of the app (optional, but good for redeployments)
                    // This is a simple way to kill a process listening on port 5000.
                    // In a production setup, you'd use a proper process manager (e.g., systemd, supervisord)
                    // or container orchestration (Docker Compose, Kubernetes).
                    sh 'fuser -k 5000/tcp || true' // Kills process using port 5000, '|| true' prevents pipeline failure if no process is found

                    // 3. Start the Flask application in the background
                    // IMPORTANT: We need to bind to 0.0.0.0 to make it accessible from outside the server.
                    // We also use 'nohup' and '&' to run it in the background after the Jenkins job finishes.
                    // 'FLASK_APP=app.py' tells Flask which file to run.
                    // 'FLASK_RUN_HOST=0.0.0.0' makes it accessible externally.
                    // 'FLASK_RUN_PORT=5000' specifies the port.
                    // 'nohup ... > app.log 2>&1 &' redirects output to a log file and runs in background.
                    sh 'FLASK_APP=app.py FLASK_RUN_HOST=0.0.0.0 FLASK_RUN_PORT=5000 nohup python -m flask run > app.log 2>&1 &'

                    echo "Flask application started on port 5000."
                    echo "Please ensure port 5000 is open in your server's firewall/security group."
                }
            }
        }
    }
}
