pipeline {
    agent any

    environment {
        NODE_ENV = 'production'  // Set the environment to production
    }

    stages {
        stage('Install Dependencies') {
            steps {
                script {
                    // Install npm dependencies
                    sh 'npm install'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // Run npm tests
                    sh 'npm test'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Build your application (optional)
                    // Add build commands here if necessary, e.g. sh 'npm run build'
                }
            }
        }

        stage('Stop Existing Application') {
            steps {
                script {
                    // Stop the running Node.js application if it's already running
                    // Adjust this command to match your process management strategy
                    sh 'pkill node || true'
                }
            }
        }

        stage('Deploy Application') {
            steps {
                script {
                    // Start the application with Node.js
                    sh 'nohup node index.js > output.log 2>&1 &'
                }
            }
        }
    }

    post {
        always {
            // Clean workspace after build
            cleanWs()
        }
        success {
            echo 'Deployment succeeded!'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
}
