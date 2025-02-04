pipeline {

    agent any

    parameters {
        string(name: 'VERSION', defaultValue: '1.0.0', description: 'Enter the application version')
        // extendedChoice(name: 'SELECTED_VALUES', 
        //                type: 'PT_CHECKBOX', 
        //                multiSelectDelimiter: ',', 
        //                value: 'Option1,Option2,Option3,Option4', 
        //                description: 'Select multiple options')
       
    }

    stages {
        stage('Build') {
            steps {
                echo "Building version: ${params.VERSION}"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying to ${params.SELECTED_VALUES} Market..."
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
