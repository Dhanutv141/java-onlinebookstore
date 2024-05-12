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
                deploy adapters: [tomcat9(credentialsId: '6c36e5da-8bb6-4bda-8ce8-53aae0c08d0b', path: '', url: 'http://34.227.90.67:8080')], contextPath: null, war: '**/*.war'
                
				
  
            }
        }
    }
				
}
