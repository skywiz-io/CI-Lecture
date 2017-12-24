pipeline { 
    agent any
    stages {
        stage('PHP Unittest') {
            steps {
                echo "Running PHP Test"
                bat 'php *.php'
            } 
        }
        stage('Create VM For QA') {
            steps {
                echo "Creating VM For QA"
            }
        }
	    stage('Wait for Manual QA') {
            steps {
                echo "Waiting for manual QA"
            }    
        }
        stage('Deploy on Prod') {
            steps {
                echo "Deploying on prod"
            }    
        }
    }
    post {
        always {
            // Shutdown the environment
            echo "Finished"
        }
        success {
            // Send Success mail message And Depoly the same version on Test project for manual QA
            echo "Success"
        }
        failure {
            //Remove Image from repo and Send Failure message
            echo "Failure"
      }
    }
}