pipeline{
    agent any
   tools{
	maven 'maven3'
    }
    stages{
       stage('GetCode'){
            steps{
                git branch: 'main', url: 'https://github.com/Dhanutv141/java-onlinebookstore.git'
            }
         }        
       stage('Build'){
            steps{
                sh 'mvn clean package'
            }
         }
        stage('SonarQube analysis') {
//    def scannerHome = tool 'SonarScanner 4.0';
        steps{
        withSonarQubeEnv('sonarqube-v10.5.1') { 
        // If you have configured more than one global server connection, you can specify its name
//      sh "${scannerHome}/bin/sonar-scanner"
        sh "mvn sonar:sonar"
    }
        }
        }
       
    }
}			

