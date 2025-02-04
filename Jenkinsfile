pipeline {

    agent any

    parameters {
        string(name: 'VERSION', defaultValue: '1.0.0', description: 'Enter the application version')
         text(name: 'SELECTED_MARKETS', defaultValue: 'US,UK', description: 'Auto-filled with selected markets')
       
    }

    stages {
        stage('Build') {
            steps {
                echo "Building version: ${params.VERSION}"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying to ${params.SELECTED_MARKETS} Market..."
                sh "python3 demoPython.py ${params.VERSION} ${params.SELECTED_MARKETS}"
            }
        }
    }

    post {
        success {
            echo 'Build and Deployment completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
