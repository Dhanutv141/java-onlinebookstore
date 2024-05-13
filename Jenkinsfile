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
                deploy adapters: [tomcat9(credentialsId: 'd708dee3-94e3-42ec-b737-3aa7b8184202', path: '', url: 'http://18.234.46.170:8080/')], contextPath: null, war: '**/*.war'
                
				
  
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
				

