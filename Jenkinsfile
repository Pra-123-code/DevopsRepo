pipeline {
    agent any  // This runs on any available agent (master or slave)

    environment {
        STAGING_SERVER = 'deploy@192.168.1.100'
        PROD_SERVER = 'deploy@192.168.1.200'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning code from repository...'
                git branch: 'main', url: 'https://github.com/your-username/your-repo.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Running build process...'
                sh './build.sh'  // Replace with your actual build command
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh './test.sh'  // Replace with your actual test command
            }
        }

        stage('Deploy to Staging') {
            when {
                branch 'main'
            }
            steps {
                echo 'Deploying to staging environment...'
                sh './deploy_staging.sh'  // Replace with your actual deploy command
            }
        }

        stage('Approval') {
            input {
                message "Do you want to deploy to Production?"
                ok "Deploy Now"
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment...'
                sh './deploy_production.sh'  // Replace with your actual deploy command
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
