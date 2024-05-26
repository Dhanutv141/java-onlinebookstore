pipeline {
    agent any
    tools {
        maven 'Maven3'
    }
    environment {
        SCANNER_HOME = tool 'sonarqube'
    }
    stages {
        stage('Git checkout') {
            steps {
               git branch: 'main', url: 'https://github.com/Dhanutv141/java-onlinebookstore.git'
            }
        }
        stage('Compile') {
            steps {
                sh 'mvn clean compile'
            }
        }
        stage('Sonarqube Analysis') {
            steps {
                sh """$SCANNER_HOME/bin/sonar-scanner\
                    -X \
                    -Dsonar.projectKey=sonar_project \
                    -Dsonar.projectName=sonar_project \
                    -Dsonar.java.binaries=target/classes \
                    -Dsonar.url=http://34.229.137.146:9000 \
                    -Dsonar.login=sqp_30a52e907937ce591076db9122e53da1f88d7f72"""
            }
        }
        stage('OWASP SCAN') {
            steps {
                dependencyCheck additionalArguments: '--scan ./', odcInstallation: 'Dp'
                dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }
        stage('Build Application') {
            steps {
                sh "mvn clean install -DskipTests"
            }
        }
    }
}

