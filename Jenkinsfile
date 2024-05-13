pipeline {
    agent any
	tools {
	    maven 'Maven3'
	}
    stages {
        stage('checkout') {
            steps {
                // Checkout the code from your repository
                git branch: 'main', url: 'https://github.com/Dhanutv141/java-onlinebookstore.git'
            }
        }
        
        stage('Build') {
            steps {
                // Build your artifact (e.g., compile code, run tests)
                sh "mvn clean install"
            }
        }

        stage('Deploy') {
            steps {
                ddeploy adapters: [tomcat9(credentialsId: '1baf45f6-e3f4-4b17-91bd-f3099220f5e4', path: '', url: 'http://35.174.6.253:8080/')], contextPath: null, war: '**/*.war'
				
  
            }
        }
		stage('Notification') {
            steps {
   				
                slackSend (
                    channel: '#jenkins',
                    message: 'Deployment successful! :tada:',
                )
            }
        }
    }

    post {
        success {
            
            echo 'Pipeline executed successfully!'
        }
        failure {
            
            echo 'Pipeline execution failed!'
        }
    }
	}
				

