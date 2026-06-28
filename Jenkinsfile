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
    script {
        try {
            emailext(
                to: "zozowaleed122@gmail.com",
                subject: "Jenkins Build Failed",
                body: "This is a test email."
            )
            echo "Email sent successfully."
        } catch (Exception e) {
            echo "Email failed: ${e.getMessage()}"
            throw e
        }
    }
}
    }
}
