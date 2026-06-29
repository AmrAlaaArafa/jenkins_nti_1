@Library('jenkins-shared-lib') _

pipeline {
    agent any // Runs the pipeline on any available executor/agent

    stages {
        stage('Hello World') {
            steps {
              sh 'chmod +x hello.sh'  
              sh './hello.sh'
            }
            
        }
        stage('Send Greeting') {
            steps {
                // Call the shared library function
                greet('You are doing great, keep learning!')
            }
      
        }
    }
    
}
