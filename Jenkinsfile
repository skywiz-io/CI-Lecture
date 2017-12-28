pipeline { 
    agent any
    stages {
        stage('PHP Unittest') {
            steps {
                echo "Running PHP Test"
                bat 'c:\\php\\php index.php'
            } 
        }
        stage('Create VM For QA') {
            steps {
                echo "Creating VM For QA"
		//build "hello vRA"
            }
        }
	    stage('Wait for Manual QA') {
            steps {
                echo "Waiting for manual QA"
            }    
        }
        stage('Deploy on Prod') {
            steps {
		input 'Do you approve deployment?'
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
