pipeline {

    agent any

    parameters {
        string(name: 'VERSION', defaultValue: '1.0.0', description: 'Enter the application version')

        choice(name: 'MARKET', choices: [
            'US', 
            'UK', 
            'Germany', 
            'France', 
            'India', 
            'China', 
            'Brazil', 
            'Japan', 
            'Australia', 
            'Canada'
        ], description: 'Select the Market for Deployment')
    }

    stages {
        stage('Build') {
            steps {
                echo "Building version: ${params.VERSION}"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying to ${params.MARKET} Market..."
                sh "python3 script.py ${params.VERSION} ${params.MARKET}"
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
