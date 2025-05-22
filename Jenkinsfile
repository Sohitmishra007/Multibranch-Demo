// Jenkinsfile

pipeline {
    // Defines the agent where the pipeline will run.
    // 'any' means Jenkins will pick any available agent.
    // For Python, you might specify a specific agent with Python installed,
    // e.g., agent { label 'python-agent' } or use a Docker agent.
    agent any

    stages {
        // Stage 1: Checkout the source code from SCM (e.g., Git)
        stage('Checkout') {
            steps {
                // Checks out the code from the configured SCM (e.g., the Git repository linked to the Jenkins job).
                checkout scm
                // Echoes the branch name for informational purposes.
                echo "Checked out branch: ${env.BRANCH_NAME}"
            }
        }

        // Stage 2: Build the application (install dependencies for Python)
        stage('Build') {
            steps {
                echo "Setting up Python environment and installing dependencies..."
                script {
                    // Create a Python virtual environment for isolated dependencies.
                    // This is good practice to avoid conflicts with system-wide Python packages.
                    sh 'python3 -m venv venv'
                    // Activate the virtual environment and install dependencies from requirements.txt.
                    // 'set +x' is used to prevent echoing the sensitive virtual environment activation command.
                    // 'set -x' is re-enabled afterwards for debugging.
                    sh 'set +x; source venv/bin/activate; set -x; pip install -r requirements.txt'
                    echo "Python dependencies installed."
                }
            }
        }

        // Stage 3: Run Tests
        // This stage is crucial for ensuring code quality.
        // For a simple demo, we don't have tests, but in a real app, you would.
        stage('Test') {
            steps {
                echo "Running tests..."
                script {
                    // Activate the virtual environment before running tests.
                    sh 'set +x; source venv/bin/activate; set -x;'
                    // Placeholder for actual test commands.
                    // If you had tests (e.g., using pytest), you'd run them here:
                    // sh 'pytest'
                    // For now, we'll just echo a message.
                    sh 'echo "No specific tests defined for this demo, but this is where they would run."'
                }
            }
        }

        // Stage 4: Deploy the application
        // This stage typically deploys to a target environment (e.g., a server, a cloud service).
        // The 'when' condition ensures this stage only runs for the 'main' branch.
        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                echo "Deploying application from main branch..."
                script {
                    // Activate the virtual environment.
                    sh 'set +x; source venv/bin/activate; set -x;'

                    // --- Deployment Options ---
                    // Option 1: Simple local run (for demonstration/testing within Jenkins)
                    // This will start the Flask app. You'd typically need a way to keep it running
                    // or deploy it to a proper server. This is NOT for production.
                    // sh 'nohup python app.py > app.log 2>&1 &'
                    // echo "Flask app started in background (for demo purposes)."

                    // Option 2: Build a Docker image (Recommended for production)
                    // This assumes you have a Dockerfile in your repository.
                    // sh 'docker build -t my-flask-app:latest .'
                    // sh 'docker push my-flask-app:latest' // Push to a Docker registry

                    // Option 3: Deploy to a cloud provider (e.g., Heroku, AWS Elastic Beanstalk, Google Cloud Run)
                    // This would involve specific commands for your chosen cloud service.
                    // Example for Heroku:
                    // sh 'heroku container:push web -a your-heroku-app-name'
                    // sh 'heroku container:release web -a your-heroku-app-name'

                    // For this simple demo, we'll just echo a deployment message.
                    echo "Application would be deployed here. For a real deployment, consider Dockerization and a proper orchestration tool or cloud service."
                    echo "Deployment completed (placeholder)."
                }
            }
        }
    }
}
