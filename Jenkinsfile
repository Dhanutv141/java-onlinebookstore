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
                deploy adapters: [tomcat9(credentialsId: '6af9e59b-963e-4cf2-beab-cebe1f2745fc', path: '', url: 'http://54.90.4.183:8080/')], contextPath: null, war: '**/*.war'
                
				
  
            }
        }
		stage('Notification') {
            steps {
   				
                slackSend (
                    channel: 'random',
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
				
}

