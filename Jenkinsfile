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
                deploy adapters: [tomcat9(credentialsId: '8157d156-4094-40d1-a6f7-440ba239a4bf', path: '', url: 'http://3.84.255.189:8080/')], contextPath: null, war: '**/*.war'
				
  
            }
        }
    }
				
}
