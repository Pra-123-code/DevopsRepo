pipeline {
    agent any  // Runs on any available node

    stages {
        stage('Build') {
            steps {
                script {
                    try {
                        echo 'Building...'
                        // Your build commands here
                    } catch (Exception e) {
                        echo "Build failed: ${e.message}"
                        currentBuild.result = 'FAILURE'
                    }
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    try {
                        echo 'Testing...'
                        // Your test commands here
                    } catch (Exception e) {
                        echo "Test failed: ${e.message}"
                        currentBuild.result = 'FAILURE'
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    try {
                        echo 'Deploying...'
                        // Your deployment commands here
                    } catch (Exception e) {
                        echo "Deployment failed: ${e.message}"
                        currentBuild.result = 'FAILURE'
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
        always {
            echo 'This will run regardless of success or failure.'
        }
    }
}
