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
		slackSend color: 'good', message: "Waiting for QA Approval. ${BUILD_URL}/input/"
		input 'Do you approve deployment?'
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
	    slackSend color: 'good', message: "Greate success. ${BUILD_URL}"
        }
        failure {
            //Remove Image from repo and Send Failure message
            echo "Failure"
	    slackSend color: 'danger', message: "Failue. ${BUILD_URL}"
            
      }
    }
}
