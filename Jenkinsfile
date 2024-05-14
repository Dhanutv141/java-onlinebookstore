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
                deploy adapters: [tomcat9(credentialsId: 'f33859d0-c8d1-41b5-be15-e833f362e00c', path: '', url: 'http://54.172.98.140:8080/')], contextPath: null, war: '**/*.war'
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
				

