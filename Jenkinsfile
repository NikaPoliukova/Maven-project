pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube_Server') {
                    sh 'mvn sonar:sonar'
                }
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                sh 'cp target/your-app.war /path/to/tomcat/webapps'
            }
        }
    }
}