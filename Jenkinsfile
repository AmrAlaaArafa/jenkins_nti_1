pipeline {
    agent any

    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['dev', 'stg', 'prod'],
            description: 'Select the environment'
        )
    }

    stages {
        stage('Hello World') {
            steps {
                echo "Hello World from trigger ${params.ENVIRONMENT}"
            }
        }

        stage('Hello Jenkins') {
            steps {
                echo "Hello Jenkins from ${params.ENVIRONMENT}"
                error("Intentional error")
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            emailext(
            to: 'zozowaleed122@gmail.com',
            subject: "❌ Jenkins Build Failed: ${env.JOB_NAME}",
            body: """
Hello,

Your Jenkins pipeline has failed.

Job Name: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Environment: ${params.ENVIRONMENT}

Build URL:
${env.BUILD_URL}

Regards,
Jenkins
"""
        )
        }
    }
}
