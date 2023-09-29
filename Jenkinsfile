pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

    stage('Build and Analyze') {
               steps {
                     bat 'mvn clean verify sonar:sonar -Dsonar.projectKey=Maven-project -Dsonar.projectName="Maven-project" -Dsonar.host.url=http://localhost:9000 -Dsonar.login=sqa_e5fc5c4dca99b5a81d86e3de45e77da40bb8f845'
               }
           }


        stage('Deploy to Tomcat') {
            steps {
                bat 'xcopy /Y /Q target\\*.war %CATALINA_HOME%\\webapps\\'
                 }
        }
    }
}